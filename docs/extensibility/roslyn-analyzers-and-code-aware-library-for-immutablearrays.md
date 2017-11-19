---
title: "Roslyn 分析器和 ImmutableArrays 感知程式碼程式庫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b33516bd013f744813b2fdb357f224bcb0d9822
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn 分析器和 ImmutableArrays 感知程式碼程式庫

[.NET 編譯器平台](https://github.com/dotnet/roslyn)("Roslyn") 可協助您建置感知程式碼程式庫。  感知程式碼的程式庫提供您可以使用的功能和工具 （Roslyn 分析器），可協助您使用程式庫中的最佳方式，或為了避免發生錯誤。  本主題說明如何建置使用時，攔截常見錯誤真實世界 Roslyn 分析器[System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet 封裝。  此範例也示範如何提供分析器所發現的程式碼問題的程式碼修正。  使用者會看到 Visual Studio 燈泡 UI 中的程式碼修正，並自動套用修正程式碼。

## <a name="getting-started"></a>快速入門

下列命令以建置這個範例，您需要：

* Visual Studio 2015 (非 Express Edition) 或更新版本。  您可以使用免費[Visual Studio Community 版本](https://www.visualstudio.com/products/visual-studio-community-vs)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  您也可以當您安裝 Visual Studio，檢查 常見工具同時安裝 SDK 的 Visual Studio 擴充性工具。  如果您已安裝 Visual Studio，您也可以安裝此 SDK 移至主功能表**檔案 &#124;新 &#124;專案...**，在左側瀏覽窗格中，選擇 C#，然後選擇 擴充性。  當您選擇 「**安裝 Visual Studio 擴充性工具**"階層連結專案範本，它會提示您下載並安裝 SDK。
* [.NET 編譯器平台 ("Roslyn") SDK](http://aka.ms/roslynsdktemplates)。  您也可以安裝此 SDK，移至主功能表**檔案 &#124;新 &#124;專案...**、 選擇**C#**左瀏覽窗格中，然後選擇**擴充性**。  當您選擇 「**下載.NET 編譯器平台 SDK**"階層連結專案範本，它會提示您下載並安裝 SDK。  此 SDK 包含[Roslyn 語法視覺化檢視](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)。  這非常有用的工具可協助您找出哪些程式碼模型類型您應該尋找在您的分析器。  分析器基礎結構會呼叫您的程式碼的特定程式碼模型類型，因此您的程式碼只執行必要時可以只著重於分析相關的程式碼。

## <a name="whats-the-problem"></a>是什麼問題？

假設您的程式庫提供 ImmutableArray (例如， <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) 支援。  C# 開發人員有許多的經驗，只要使用.NET 陣列。  不過，由於 ImmutableArrays 和最佳化的技術，用於實作的本質，C# 開發人員 intuitions 會導致使用者的程式庫撰寫中斷的程式碼，如下所述。  此外，使用者不會看到其錯誤到執行階段，這並不是它們用來在 Visual Studio.net 中的高品質體驗。

使用者很熟悉撰寫程式碼如下所示：

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

建立空的陣列，以填入後續幾行程式碼和使用集合初始設定式語法是 C# 開發人員非常熟悉。  不過，撰寫相同程式碼的 ImmutableArray 損毀在執行階段：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

第一個錯誤是因為 ImmutableArray 實作使用包裝的基礎資料存放區結構。 結構必須具有無參數建構函式，讓`default(T)`運算式可能會傳回所有的結構零或 null 的成員。  當程式碼存取`b1.Length`，沒有執行的階段 null 取值錯誤，因為 ImmutableArray 結構中沒有任何基礎的存放裝置陣列。  若要建立空的 ImmutableArray 的正確方式是`ImmutableArray<int>.Empty`。

因為 ImmutableArray.Add 方法傳回的新執行個體每次呼叫時，就會發生與集合初始設定式錯誤。  由於 ImmutableArrays 永遠不會變更，當您將加入新項目，您會回到新的 ImmutableArray 物件 （其中可能會與先前已存在的 ImmutableArray 共用儲存區，基於效能的考量）。  因為`b2`指向第一個呼叫之前 ImmutableArray`Add()`五次，`b2`的預設 ImmutableArray。  長度上呼叫它也為 null 的當機取值 （dereference) 的錯誤。  初始化 ImmutableArray，而不以手動方式呼叫 新增来使用的正確方式`ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`。

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>尋找相關的語法節點型別來觸發您分析器

 若要開始建置分析器，先找出您要尋找的 SyntaxNode 類型。 啟動語法視覺化檢視，從功能表**檢視 &#124;其他視窗 &#124;Roslyn 語法視覺化檢視**。

將編輯器插入號放在宣告行`b1`。  您會看到語法視覺化檢視會顯示您在`LocalDeclarationStatement`語法樹狀結構的節點。  這個節點有`VariableDeclaration`，因而具有`VariableDeclarator`，因而具有`EqualsValueClause`，而且最後沒有`ObjectCreationExpression`。  當您按一下在語法視覺化檢視樹狀目錄中的節點，[編輯器] 視窗中的語法反白顯示，以顯示該節點所代表的程式碼。  SyntaxNode 子類型的名稱符合 C# 文法中使用的名稱。

## <a name="creating-the-analyzer-project"></a>建立分析器專案

從主要功能表選擇 **檔案 &#124;新 &#124;專案...**.在**新專案**對話方塊下方**C#**專案如果您在左側的導覽列中，選擇 擴充性，並在右窗格中選擇**與修正程式碼分析器**專案範本。  輸入名稱，並確認對話方塊。

範本開啟 DiagnosticAnalyzer.cs 檔案。  選擇該編輯器緩衝區 索引標籤。此檔案具有分析器類別 (形成您為資料庫專案的名稱)，衍生自`DiagnosticAnalyzer`（Roslyn 應用程式開發介面型別）。  您新的類別必須`DiagnosticAnalyzerAttribute`宣告您分析器是適用於 C# 語言，如此，編譯器會探索並載入您的分析師。

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

您可以實作使用 C# 程式碼，為目標的 Visual Basic 分析器，反之亦然。  它是選擇您的分析目標一種語言，或兩者都 DiagnosticAnalyzerAttribute 中更重要。  更趨精密完美的分析器需要詳細的語言模型可以只為目標單一語言。  如果您的分析師，比方說，只會檢查類型名稱或公用成員名稱，可能無法使用通用 Roslyn 提供跨 Visual Basic 和 C# 語言模型。  比方說，FxCop 提出警告類別會實作<xref:System.Runtime.Serialization.ISerializable>，但類別沒有<xref:System.SerializableAttribute>屬性與語言無關，而且適用於 Visual Basic 和 C# 程式碼。

## <a name="initalizing-the-analyzer"></a>初始化 Part-of-speech 分析器

 中向下捲動有點`DiagnosticAnalyzer`類別，以查看`Initialize`方法。  啟用分析器時，編譯器會呼叫這個方法。  這個方法會接受`AnalysisContext`物件，可讓您分析師取得內容的資訊，並註冊您想要分析的程式碼種類的事件回呼。

```csharp
public override void Initialize(AnalysisContext context) {}

```

開啟新的一行中這個方法和類型 「 內容 」。 若要查看的 IntelliSense 完成清單。  您所見，完成清單中有許多`Register...`方法來處理各種類型的事件。  例如，第一個， `RegisterCodeBlockAction`，您的程式碼區塊，通常是大括號之間的程式碼呼叫。  正在註冊的區塊也會呼叫回您的程式碼初始設定式的欄位、 屬性、 指定的值或選擇性參數的值。

另舉一例， `RegisterCompilationStartAction`，呼叫您的程式碼在編譯時，您需要透過許多位置收集狀態的開頭。  您可以建立資料結構，例如收集所有符號的使用，而且您分析器回呼部分語法或符號，每次可以儲存每個位置的相關資訊，在您的資料結構中。  由於編譯結束正在傳回進行呼叫，您可以分析您儲存，比方說，若要報告程式碼會從每個使用何種符號的所有位置`using`陳述式。

使用**語法視覺化檢視**，您已了解您想要在編譯器處理 ObjectCreationExpression 時呼叫。  您可以使用此程式碼來設定回呼：

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

您註冊語法節點和只有物件建立語法節點的篩選條件。  依照慣例，分析器作者會使用 lambda，註冊有助於保護分析器無狀態的動作時。  您可以使用 Visual Studio 功能**從使用量產生**建立`AnalyzeObjectCreation`方法。  這會產生正確的內容參數類型為您太。

## <a name="setting-properties-for-users-of-your-analyzer"></a>您的分析師的使用者設定的屬性

讓您分析程式會出現在 Visual Studio UI 適當，尋找並修改下列程式碼來識別您的分析師：

```csharp
internal const string Category = "Naming";
```

Change `"Naming"` to `"API Guidance"`.

下一個尋找並開啟`Resources.resx`檔案在專案中使用**方案總管 中**。  您可以將描述您的分析師、 標題等。您可以變更所有的這些值`"Don't use ImmutableArray<T> constructor"`現在。  您可以將字串格式 （{0}、 {1} 等），在字串中的引數和更新版本，當您呼叫`Diagnostic.Create()`，您可以提供`params`要傳遞引數的陣列。

## <a name="analyzing-an-object-creation-expression"></a>分析的物件建立運算式

`AnalyzeObjectCreation`方法會採用不同類型的程式碼分析器架構所提供的內容。  Initialize 方法`AnalysisContext`可讓您註冊動作來設定您的分析師的回呼。  `SyntaxNodeAnalysisContext`，例如，具有`CancellationToken`周圍，您可以傳遞。  如果使用者啟動時輸入在編輯器中，Roslyn 將會取消執行分析器，以儲存工作並改善效能。  另舉一例，此內容會有一個傳回的物件建立語法節點的節點屬性。

取得節點中，您可以假設您已篩選的語法節點動作的類型：

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>使用您的分析程式第一次啟動 Visual Studio

藉由建置並執行您的分析師啟動 Visual Studio (按**F5**)。  因為專案中的啟動**方案總管 中**是 VSIX 專案，您的程式碼和 VSIX 中，執行您的程式碼的組建，便會啟動 Visual Studio 使用該安裝的 VSIX。  當您以這種方式啟動 Visual Studio 時，它會啟動具有相異的登錄區，讓您的 Visual Studio 的主要用途將不會影響您的測試執行個體時建立分析器。  第一次啟動這種方式，Visual Studio 會執行類似於當您第一次啟動 Visual Studio 安裝它之後的數個初始設定。

建立主控台專案，並在您主控台應用程式的 Main 方法中輸入陣列的程式碼：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

程式碼行`ImmutableArray`有波浪線，因為您需要取得不可變的 NuGet 封裝，再將`using`陳述式，以您的程式碼。  中的專案節點上按右指標按鈕**方案總管 中**選擇**管理 NuGet 封裝...**.在 NuGet 管理員中，在 搜尋 方塊中，輸入 「 不可 」 變更和選擇的項目 」 System.Collections.Immutable"（不選擇"Microsoft.Bcl.Immutable"） 在左的窗格中按右窗格中的 安裝 按鈕。  安裝封裝會將您的專案參考的參考。

您仍看見底下的紅色波浪線`ImmutableArray`，因此將插入號放在該識別項和按**CTRL +。** （句號），顯示建議的修正程式功能表，然後選擇加入適當`using`陳述式。

**全部儲存並關閉**能讓您在乾淨狀態繼續目前的 Visual Studio 的第二個執行個體。

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>完成分析師使用編輯後繼續

在 Visual Studio 的第一個執行個體，設定中斷點的開頭您`AnalyzeObjectCreation`按方法**F9**使用插入號上的第一行。

啟動一次使用您分析器**F5**，和在 Visual Studio 的第二個執行個體，重新開啟您最後一次建立主控台應用程式。

您會返回在中斷點的 Visual Studio 的第一個執行個體，因為 Roslyn 編譯器所看到的物件建立運算式和呼叫您的分析師。

**取得物件建立節點。** 不進入函式的行，設定`objectCreation`變數按**F10**，然後在**即時運算視窗**評估運算式`"objectCreation.ToString()"`。  您會看到變數會指向語法節點為程式碼`"new ImmutableArray<int>()"`，只會尋找的。

**取得 ImmutableArray < T\>型別物件。** 您要檢查是否正在建立的類型為 ImmutableArray。  首先，您會取得代表這個類型的物件。  您檢查以確保您完全正確的類型，而且您不要比較 tostring （） 的字串中使用語意模型的型別。  輸入下列行結尾的函式的程式碼：

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

您指定泛型型別中繼資料與 backquotes （'） 與泛型參數的數目。  這就是為什麼看不到"...ImmutableArray\<T >"中的中繼資料名稱。

語意模型上，可讓您詢問有關符號、 資料流程、 變數存留期、 等等的問題，有許多有用的項目。Roslyn 語意模型中來分隔語法節點，基於各種工程 （效能，模型錯誤的程式碼等。）。  您想要編譯模型查詢的精確的比較參考中所包含的資訊。

您可以將執行黃色指標拖曳 [編輯器] 視窗的左半部。  將它拖曳到設定的一行`objectCreation`變數和不進入函式程式碼使用您新的一行**F10**。  如果您將滑鼠指標停留在變數`immutableArrayOfType`，您會看到我們語意模型中找到正確的類型。

**取得物件建立運算式的類型。** 「 類型 」 會使用幾種方法，在本文中，但這表示如果您有"新 Foo"運算式中，您需要取得 Foo 的模型。  您要取得其類型的物件建立運算式，以查看它是否 ImmutableArray\<T > 類型。  若要取得類型符號 (ImmutableArray) 的符號資訊的物件建立運算式中再次使用語意模型。  輸入下列行結尾的函式的程式碼：

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

因為您分析器會需要處理不完整或不正確的程式碼編輯器緩衝區中 (例如，遺漏了`using`陳述式)，您應該檢查`symbolInfo`正在`null`。  您需要取得具名型別 (INamedTypeSymbol) 中的符號資訊物件，才能完成分析。

**比較類型。** 由於沒有我們要尋找的 T 為開放式泛型類型，而且程式碼中的類型是具象的泛型類型，您查詢建構 （開放式泛型類型） 從何種類型的符號資訊，並比較該結果與`immutableArrayOfTType`。  請在方法的結尾輸入：

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**回報診斷。** 報告診斷是很簡單。  您使用專案範本，其定義之前的初始化方法中，為您建立的規則。  由於這種情況下在程式碼是錯誤，您可以變更初始化規則來取代一行`DiagnosticSeverity.Warning`（綠色波浪線） 與`DiagnosticSeverity.Error`（紅色波浪線）。  此規則的其餘部分初始化從您即將開始逐步解說的編輯過的資源。  您也需要報表的位置在波浪線上，也就是物件建立透過型別規格的位置。  輸入這個程式碼的`if`區塊：

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

您的函式看起來應該像這樣 （可能是不同的格式）：

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

移除中斷點，讓您可以查看分析器工作 （並停止返回 Visual Studio 的第一個執行個體）。  執行指標拖曳至您的方法，並按下的開頭**F5**繼續執行。  當您切換回 Visual Studio 的第二個執行個體時，編譯器將會啟動一次，檢查程式碼，它就會呼叫您的分析師。  您可以看到下的波浪線`ImmutableType<int>`。

## <a name="adding-a-code-fix-for-the-code-issue"></a>加入的程式碼問題的 [程式碼修正]

開始之前，請關閉 Visual Studio 的第二個執行個體，並停止偵錯 （其中您所開發的分析器） 的 Visual Studio 的第一個執行個體中。

**加入新的類別。** 使用您在 [方案總管] 中的專案節點的捷徑功能表 （右邊的指標按鈕），然後選擇要加入新項目。  新增類別，稱為`BuildCodeFixProvider`。  這個類別必須衍生自`CodeFixProvider`，而且您必須使用**CTRL +。** （句號） 來叫用加入正確的程式碼修正`using`陳述式。  這個類別也必須標註具有`ExportCodeFixProvider`屬性，而且您將需要新增`using`陳述式來解決`LanguageNames`列舉。  您應該會在它為下列程式碼的類別檔案：

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**清除衍生的成員。** 現在，將編輯器插入號放在識別項`CodeFixProvider`按**CTRL +。** （句點） 以清除這個抽象基底類別的實作。  這會為您產生的屬性和方法。

**實作屬性。** 填寫`FixableDiagnosticIds`屬性的`get`本文中的下列程式碼：

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn 結合診斷並修正藉由比對這些識別碼，只是字串。  專案範本會產生診斷的識別碼，而且您可用來變更它。  屬性中的程式碼只會傳回從分析器類別識別碼。

**RegisterCodeFixAsync 方法取得內容。** 內容很重要的因為程式碼修正可以套用到多個診斷，或在程式碼行上可能有一個以上的問題。  如果您輸入 「 內容 」。 在方法主體中，IntelliSense 完成清單會顯示您一些有用的成員。  沒有您可以檢查的項目，是否要取消修正 CancellationToken 成員。  沒有具有許多實用的成員，並可讓您取得專案和方案的模型物件的文件成員。  範圍的成員開頭和結尾的程式碼位置指定您會在何時回報診斷。

**請為非同步方法。** 您必須進行第一件事是修正產生的方法宣告為`async`方法。  建立虛設常式的抽象類別類型的程式碼修正不包含`async`關鍵字，即使該方法會傳回`Task`。

**取得語法樹狀目錄的根目錄。** 若要修改產生新的語法樹狀結構的變更所需的程式碼可讓您的程式碼修正。  您需要`Document`內容與呼叫`GetSyntaxRootAsync`。  這是非同步方法，因為沒有未知的工作，以取得語法樹狀目錄，可能會包含從磁碟中取得檔案、 剖析，並建置 Roslyn 程式碼模型。  在此期間，使用 Visual Studio UI 應該有回應`async`啟用。  以下列內容取代方法中的程式碼行：

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**找出問題的節點。** 您要傳入的內容範圍內，但您會發現可能需要變更的程式碼的節點。  回報的診斷僅提供範圍的類型識別項 （其中波浪線所屬），但您要取代整個物件建立運算式，包括`new`關鍵字開頭和結尾的括號。  將下列程式碼加入至您的方法 (並用**CTRL +。** 若要加入`using`陳述式`ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**註冊您的燈泡 UI 的程式碼修正。** 當您註冊您的程式碼修正時，Roslyn 可插入 Visual Studio 燈泡 UI 自動。  使用者將會看到他們可以使用**CTRL +。** （句號） 當您分析師波浪線錯誤`ImmutableArray<T>`建構函式使用。  因為發生問題時，只執行您的程式碼修正提供者，您可以假設您有您要尋找的物件建立運算式。  從內容參數，您可以註冊新的程式碼修正結尾加入下列程式碼`RegisterCodeFixAsync`方法：

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

您要將編輯器插入號放在與識別`CodeAction`，然後使用**CTRL +。** （句號） 加入適當`using`此類型的陳述式。

然後將放置在編輯器插入號`ChangeToImmutableArrayEmpty`識別碼和使用**CTRL +。** 為您產生這個方法 stub。

您加入此最後一個程式碼片段會藉由傳遞登錄的程式碼修正`CodeAction`和診斷的識別碼，找到問題的種類。  在此範例中，沒有只有一個診斷的識別碼，這段程式碼提供修正程式，因此您可將傳遞診斷的識別碼陣列的第一個項目。  當您建立`CodeAction`，您要傳入燈泡 UI 應該使用做為程式碼修正描述的文字。  您也將會接受 CancellationToken 並傳回新的文件的函式中傳遞。  新的文件有新的語法樹狀目錄，其中包含您的修補程式碼呼叫`ImmutableArray.Empty`。  此程式碼片段會使用 lambda，讓它可以透過 objectCreation 節點和內容的文件關閉。

**建構新的語法樹狀結構。** 在`ChangeToImmutableArrayEmpty`您稍早所產生的虛設常式輸入的一行程式碼的方法： `ImmutableArray<int>.Empty;`。  如果您再次檢視語法視覺化檢視工具視窗，您可以看到這個語法是 SimpleMemberAccessExpression 節點。  這是這個方法需要建構及傳回新的文件中。

第一個變更`ChangeToImmutableArrayEmpty`是加入`async`之前`Task<Document>`因為程式碼產生器不能假設方法應該是非同步。

使您的方法看起來類似下面的填入取代下列程式碼主體：

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

您必須將編輯器插入號放在`SyntaxGenerator`識別碼和使用**CTRL +。** （句號） 加入適當`using`此類型的陳述式。

此程式碼使用`SyntaxGenerator`，這是一種非常好用來建構新的程式碼。  取得文件產生器擁有的程式碼問題之後,`ChangeToImmutableArrayEmpty`呼叫`MemberAccessExpression`、 傳遞有我們想要存取之的成員的類型和成員的名稱傳遞為字串。

接下來，此方法會擷取的文件根，因為這可能包含任意的工作，在一般情況下，此程式碼等候此呼叫，並傳遞取消語彙基元。  Roslyn 程式碼模型是不可變的類似於處理.NET 字串;當您更新字串時，會傳回取得新的 string 物件。  當您呼叫`ReplaceNode`，您會回到新的根節點。  大部分的語法樹狀目錄的共用 （因為它是不可變），但`objectCreation`節點取代`memberAccess` 節點，以及最多的語法樹狀結構根目錄的所有父節點。

## <a name="trying-your-code-fix"></a>嘗試您的程式碼修正

您現在可以按**F5**要在 Visual Studio 的第二個執行個體中執行您的分析師。  開啟您以前使用的主控台專案。  現在您應該會看到燈泡出現新的物件建立運算式的`ImmutableArray<int>`。  如果您按下**CTRL +。** （時間），則您會看到您的程式碼修正，，您會看到燈泡 UI 中的自動產生的程式碼差異預覽。  Roslyn 為您建立此。

**Pro 提示：**如果啟動 Visual Studio 中，第二個執行個體，而且您未看到燈泡和您的程式碼修正，則您可能需要清除 Visual Studio 元件快取。  清除快取會強制重新檢查元件，讓 Visual Studio 應該會挑選您最新的元件的 Visual Studio。  首先，請關閉 Visual Studio 的第二個執行個體。  然後在 Windows 檔案總管，前往 使用者目錄 (c:\users\\< userid\>)，並尋找 AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\。  在此目錄中，刪除子目錄 ComponentModelCache。  版本與 Visual Studio"14"變更。

## <a name="talk-video-and-finish-code-project"></a>Talk 視訊及完成程式碼專案

您可以看到開發，並討論此範例中進一步[此 talk](http://channel9.msdn.com/events/Build/2015/3-725)。  Talk 示範使用分析程式，並引導您建立它。

您可以看到所有完成的程式碼[這裡](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)。  DoNotUseImmutableArrayCollectionInitializer 和 DoNotUseImmutableArrayCtor 每一個子資料夾具有找出問題並實作顯示在 Visual Studio 燈泡 UI 的程式碼修正程式的 C# 檔案的 C# 檔案。  請注意，完成的程式碼具有極小的多個抽象概念，以避免擷取 ImmutableArray\<T > 一再輸入物件。  它使用巢狀的已註冊的動作所使用的內容中儲存的型別物件時的子動作 （分析物件建立和分析集合初始設定） 執行。

## <a name="see-also"></a>另請參閱

* [\\\Build 2015 talk](http://channel9.msdn.com/events/Build/2015/3-725)
* [GitHub 上的完整程式碼](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [在 GitHub 上的數個範例會分組為三種類型的分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS 站台上的其他文件](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [實作與 Roslyn 分析器 GitHub 上的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
