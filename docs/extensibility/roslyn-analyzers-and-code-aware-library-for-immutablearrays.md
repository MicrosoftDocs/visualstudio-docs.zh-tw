---
title: Roslyn 分析器和程式碼感知程式庫，適用於 Immutablearray |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d6b603a59ad27052ab8eb9bbb88942584aa5293
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000896"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn 分析器和程式碼感知程式庫，適用於 Immutablearray

[.NET 編譯器平台](https://github.com/dotnet/roslyn)("Roslyn") 可協助您建置程式碼感知程式庫。 程式碼感知程式庫會提供您可以使用的功能和工具 （Roslyn 分析器），可協助您使用程式庫，以最佳方式，或避免發生錯誤。 本主題說明如何建置來攔截最常見錯誤時使用的真實世界 Roslyn 分析器[System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet 套件。 此範例也會示範如何提供分析器所找到的程式碼問題的程式碼修正。 使用者會看到 Visual Studio 燈泡 UI 中的程式碼修正，並可以自動套用修正程式碼。

## <a name="get-started"></a>開始使用

您需要下列項目來建置此範例中：

* Visual Studio 2015 (非 Express Edition) 或更新版本。 您可以使用免費[Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 您也可以 Visual Studio，安裝時檢查**Visual Studio Extensibility Tools**下方**常見工具**同時安裝 SDK。 如果您已安裝 Visual Studio，您也可以安裝此 SDK 移至主功能表**檔案** > **新增** > **專案**，選擇**C#** 左瀏覽窗格中，然後選擇**擴充性**。 當您選擇 「**安裝 Visual Studio Extensibility Tools**"階層連結專案範本，它會提示您下載並安裝 SDK。
* [.NET 編譯器平台 ("Roslyn") SDK](http://aka.ms/roslynsdktemplates)。 您也可以安裝此 SDK 移至主功能表**檔案** > **新增** > **專案**選擇**C#** 左瀏覽窗格中，然後選擇**擴充性**。 當您選擇 「**下載.NET Compiler Platform SDK**"階層連結專案範本，它會提示您下載並安裝 SDK。 此 SDK 包含[Roslyn 語法視覺化檢視](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)。 這個實用的工具會協助您找出哪些程式碼模型類型您應該尋找在您的分析器。 分析器基礎結構會呼叫您的程式碼對於特定的程式碼模型型別，因此您的程式碼只會在必要時執行，並可以只著重於分析相關的程式碼。

## <a name="whats-the-problem"></a>是什麼問題？

想像一下您的程式庫提供 ImmutableArray (比方說， <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) 支援。 C# 開發人員有豐富經驗的.NET 陣列。 不過，由於用於 Immutablearray 和最佳化的技術實作中使用的本質，C# 開發人員 intuitions 會導致使用者程式庫撰寫中斷的程式碼，如下所述。 此外，使用者不會看到其錯誤到執行階段，這並不是他們用來在 Visual Studio 中使用.NET 的高品質體驗。

使用者熟悉撰寫程式碼，如下所示：

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

建立空的陣列，以填入接下來的幾行程式碼，並使用集合初始設定式語法很熟悉C#開發人員。 不過，撰寫相同 ImmutableArray 的程式碼損毀在執行階段：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

第一個錯誤是因為 ImmutableArray 的實作來包裝基礎資料儲存區使用的結構。 結構必須具有無參數建構函式，讓`default(T)`運算式可以傳回所有結構零或 null 的成員。 當程式碼存取`b1.Length`，沒有執行的階段 null 取值的錯誤，因為 ImmutableArray 結構中沒有任何基礎的存放裝置陣列。 若要建立空的 ImmutableArray 的正確方式是`ImmutableArray<int>.Empty`。

使用集合初始設定式的錯誤是因為`ImmutableArray.Add`方法就會傳回新的執行個體，每次呼叫它。 因為用於 Immutablearray 永遠不會變更，當您新增新的項目時，您會取得新的 ImmutableArray 物件 （這可能會與先前已存在的 ImmutableArray 共用儲存體，基於效能考量）。 因為`b2`指向之前呼叫的第一個 ImmutableArray`Add()`五次，`b2`是 ImmutableArray 的預設值。 長度上呼叫它也為 null 的當機取值 （dereference) 的錯誤。 若要手動呼叫是使用未初始化的 ImmutableArray 的正確方式`ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`。

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>尋找相關的語法來觸發您的分析師的節點類型

 若要開始建置 「 分析器 」，先找出您要尋找的何種 SyntaxNode。 啟動**語法視覺化檢視**從功能表**檢視** > **其他 Windows** > **Roslyn 語法視覺化檢視**.

將編輯器插入號放在宣告行`b1`。 您會看到語法視覺化檢視會顯示您位於`LocalDeclarationStatement`語法樹狀結構的節點。 此節點已`VariableDeclaration`，其中又包含`VariableDeclarator`，其中又包含`EqualsValueClause`，最後還有`ObjectCreationExpression`。 當您按一下在語法視覺化檢視樹狀目錄中的節點，在 [編輯器] 視窗中的語法反白顯示為各位示範該節點所表示的程式碼。 SyntaxNode 子類型的名稱符合 C# 文法中使用的名稱。

## <a name="create-the-analyzer-project"></a>建立分析器專案

從主功能表中，選擇**檔案** > **新增** > **專案**。 中**新的專案**] 對話方塊底下**C#** 專案，在左側的導覽列中，選擇**擴充性**，，然後在右窗格中選擇 [**與分析器程式碼修正**專案範本。 輸入名稱，然後確認對話方塊。

範本會開啟*DiagnosticAnalyzer.cs*檔案。 選擇該編輯器緩衝區 索引標籤。此檔案具有分析器類別 (形成您為資料庫專案的名稱)，衍生自`DiagnosticAnalyzer`（Roslyn API 型別）。 您新的類別必須`DiagnosticAnalyzerAttribute`宣告您的分析器是 C# 語言相關，如此，編譯器會探索並載入您的分析器。

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

您可以實作使用 C# 程式碼，為目標的 Visual Basic 中的 analyzer，反之亦然。 它是選擇您的分析器目標一種語言，或兩者 DiagnosticAnalyzerAttribute 更重要。 更複雜的分析器需要詳細模型化的語言可以只針對茪擩槧槶。 如果您的分析器，例如，只會檢查類型名稱或公用成員名稱，它可能使用 Roslyn 提供涵蓋 Visual Basic 和 C# 通用的語言模型。 比方說，FxCop 警告類別會實作<xref:System.Runtime.Serialization.ISerializable>，但類別沒有<xref:System.SerializableAttribute>屬性與語言無關，而且適用於 Visual Basic 和 C# 程式碼。

## <a name="initialize-the-analyzer"></a>初始化 「 分析器 」

 向下捲動有點`DiagnosticAnalyzer`類別，以查看`Initialize`方法。 啟用分析器時，編譯器會呼叫這個方法。 此方法會採用`AnalysisContext`物件，可讓您的分析器，以取得內容資訊，以及如何註冊回呼事件的一種您想要分析的程式碼。

```csharp
public override void Initialize(AnalysisContext context) {}
```

開啟新的一行，在此方法並輸入 「 內容 」。 若要查看的 IntelliSense 完成清單。 您所見，完成清單中有許多`Register...`方法來處理各種類型的事件。 比方說，第一個`RegisterCodeBlockAction`，回到您的程式碼區塊，通常是大括號之間的程式碼的呼叫。 註冊的區塊也會回呼您的程式碼初始設定式的欄位、 屬性 (attribute) 來提供的值或選擇性參數的值。

另舉一例， `RegisterCompilationStartAction`，回到您的程式碼開頭的編譯中，這非常有用，當您需要收集許多位置上的狀態時呼叫。 您可以建立資料結構，例如收集所有符號使用，而且每次您分析器回呼叫的某些語法或符號，可以儲存每個位置的相關資訊，資料結構中。 當您因為在編譯結束回撥時，可以分析您儲存，比方說，若要報告哪些程式碼會從每個使用的符號的所有位置`using`陳述式。

使用**語法視覺化檢視**，您已了解您想要編譯器處理 ObjectCreationExpression 時呼叫。 您可以使用此程式碼來設定回呼：

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

您註冊語法節點，然後只物件建立語法節點的篩選條件。 依照慣例，分析器作者會使用 lambda，註冊動作，藉此讓分析器的無狀態時。 您可以使用 Visual Studio 功能**使用時產生**建立`AnalyzeObjectCreation`方法。 這會產生正確的內容參數的類型為您太。

## <a name="set-properties-for-users-of-your-analyzer"></a>您的分析師的使用者設定屬性

讓您分析程式顯示在 Visual Studio UI 適當，尋找並修改下列行程式碼，以識別您的分析器：

```csharp
internal const string Category = "Naming";
```

變更`"Naming"`至`"API Guidance"`。

接下來尋找並開啟*Resources.resx*在專案中使用的檔案**方案總管 中**。 您可以放入您的分析器、 標題等的描述。您可以變更所有的這些值`"Don't use ImmutableArray<T> constructor"`現在。 您可以放入字串格式化在字串中的引數 ({0}，{1}等)，及更新版本，當您呼叫`Diagnostic.Create()`，您可以提供`params`要傳遞的引數陣列。

## <a name="analyze-an-object-creation-expression"></a>分析物件建立運算式

`AnalyzeObjectCreation`方法會採用不同類型的程式碼分析器 framework 所提供的內容。 `Initialize`方法的`AnalysisContext`可讓您註冊動作的回呼，以便設定您的分析器。 `SyntaxNodeAnalysisContext`，例如，具有`CancellationToken`，您可以傳遞。 如果使用者會啟動在編輯器中輸入，Roslyn 會取消執行的分析器，以儲存工作，並改善效能。 另舉一例，此內容會有一個傳回的物件建立語法節點的節點屬性。

取得節點中，您可以假設您已篩選的語法節點動作的類型：

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>使用您的分析程式第一次啟動 Visual Studio

啟動 Visual Studio 建置並執行您的分析程式 (按下**F5**)。 因為啟動專案內**方案總管] 中**是 VSIX 專案，您的程式碼和 VSIX 中，執行您的程式碼的組建，然後啟動 [Visual Studio 中使用該安裝的 VSIX。 當您啟動 Visual Studio，如此一來時，它會啟動具有相異的登錄 hive，讓您的 Visual Studio 的主要用途將不會影響您測試的執行個體同時建置分析器。 第一次啟動如此一來，Visual Studio 會執行數個類似於當您第一次啟動 Visual Studio 安裝它之後的初始化。

建立主控台專案，然後輸入您主控台應用程式的 Main 方法中的陣列程式碼：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

使用程式碼行`ImmutableArray`具有波浪線，因為您要取得不可變的 NuGet 套件，並新增`using`陳述式，以您的程式碼。 中的專案節點上按右指標按鈕**方案總管**，然後選擇**管理 NuGet 套件**。 在 NuGet 管理員中，在 搜尋 方塊中，輸入 「 不可變 」，然後選擇 項目**System.Collections.Immutable** (請勿選擇**Microsoft.Bcl.Immutable**) 的左的窗格，然後按下**安裝**右窗格中的按鈕。 安裝套件將參考加入您的專案參考。

您仍然看到紅色的波浪線下`ImmutableArray`，因此將插入號放在該識別項，然後按**Ctrl**+**。** （句點），來顯示建議的修正程式功能表，然後選擇 新增適當`using`陳述式。

**全部儲存並關閉**能讓您在乾淨狀態繼續目前的 Visual Studio 的第二個執行個體。

## <a name="finish-the-analyzer-using-edit-and-continue"></a>完成分析器] 使用 [編輯後繼續

在 Visual Studio 的第一個執行個體，設定中斷點的開頭您`AnalyzeObjectCreation`方法，藉由按下**F9**使用插入號上的第一行。

啟動您的分析器，以再次**F5**，並在 Visual Studio 的第二個執行個體，重新開啟您建立最後一次您主控台應用程式。

您會回到第一個 Visual Studio 執行個體的中斷點處，因為 Roslyn 編譯器所看到的物件建立運算式，並呼叫您的分析器。

**取得物件建立節點。** 逐程序，設定`objectCreation`變數所按下**F10**，然後在**即時運算視窗**評估運算式`"objectCreation.ToString()"`。 您會看到變數所指向的語法節點是程式碼`"new ImmutableArray<int>()"`，只什麼您所需。

**取得 ImmutableArray < T\>型別物件。** 您必須檢查所建立的型別是否 ImmutableArray。 首先，您會取得代表這個類型的物件。 檢查以確保有完全正確的型別，而且您不會比較將字串從使用語意模型的型別`ToString()`。 輸入下列這一行的結尾的函式的程式碼：

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

您指定泛型型別在中繼資料，以倒引號 （'） 和泛型參數的數目。 這就是為什麼您沒有看到...ImmutableArray\<T >"中的中繼資料名稱。

語意模型上，可讓您詢問有關符號、 資料流，變數的存留期等問題，有許多有用的事情。Roslyn 會基於各種工程 （效能、 模型等錯誤的程式碼。） 分隔語意模型中的語法節點。 您想讓編譯模型查詢中進行精確比較的參考所包含的資訊。

您可以將黃色執行指標拖曳 [編輯器] 視窗的左邊。 將它拖曳至 設定在列`objectCreation`變數和不進入程式碼使用您新的一行**F10**。 如果您將滑鼠指標停留在變數`immutableArrayOfType`，您會看到我們在語意模型中找到確切的型別。

**取得物件建立運算式的類型。** 「 類型 」 會使用本文中，有幾種，但這表示如果您有 「 新的 Foo"運算式中，您需要取得 Foo 的模型。 您需要取得的物件建立運算式，以查看它是否 ImmutableArray 類型\<T > 類型。 若要取得類型符號 (ImmutableArray) 的符號資訊的物件建立運算式中，再次使用語意模型。 輸入下列這一行的結尾的函式的程式碼：

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

因為您的分析器會需要處理不完整或不正確的程式碼編輯器緩衝區中 (例如，沒有遺漏`using`陳述式)，您應檢查有無`symbolInfo`正在`null`。 您需要取得具名型別 (INamedTypeSymbol) 中的符號資訊物件，以完成分析。

**比較類型。** 因為我們要尋找的 T 的開放式泛型類型，且程式碼中的型別是具體的泛型型別，您查詢類型建構自 （開放式的泛型型別） 的符號資訊，並比較該結果`immutableArrayOfTType`。 輸入下列內容方法的結尾：

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**回報診斷。** 報告此診斷並不難。 您使用為您建立專案範本，其定義之前的初始化方法中的規則。 由於這種情況下，程式碼中的，即為錯誤，您可以變更初始化規則來取代該行`DiagnosticSeverity.Warning`（綠色波浪線） 與`DiagnosticSeverity.Error`（紅色波浪線）。 此規則的其餘部分初始化您附近的逐步解說開頭所編輯的資源。 您也需要報表的位置在波浪線上，也就是物件建立運算式的類型規格的位置。 輸入此代碼`if`區塊：

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

您的函式應該看起來像這樣 （可能是不同的格式）：

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

移除中斷點，讓您可以查看您的分析器如何運作 （和停止 Visual Studio 的第一個執行個體所傳回）。 將執行指標拖曳至您的方法，然後按開頭**F5**繼續執行。 當您切換回 Visual Studio 的第二個執行個體時，編譯器將會啟動一次，檢查程式碼，它將會呼叫您的分析器。 您可以看到下的波浪線`ImmutableType<int>`。

## <a name="adding-a-code-fix-for-the-code-issue"></a>新增 「 程式碼修正 」 的程式碼問題

在開始之前，請關閉 Visual Studio 的第二個執行個體，並停止在第一個執行個體 （其中您正在開發 「 分析器 」） 的 Visual Studio 中偵錯。

**加入新的類別。** 使用捷徑功能表 （右指標按鈕），在您的專案節點上**方案總管] 中**，然後選擇 [加入新項目。 新增類別，稱為`BuildCodeFixProvider`。 這個類別必須衍生自`CodeFixProvider`，而且您必須使用**Ctrl**+**。** （句點），來叫用加入正確的程式碼修正`using`陳述式。 這個類別也必須使用註解`ExportCodeFixProvider`屬性，而且您必須新增`using`陳述式，以解決`LanguageNames`列舉。 您應該具有下列的程式碼的類別檔案：

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**虛設常式衍生的成員。** 現在，將編輯器插入號放在識別項`CodeFixProvider`按下**Ctrl**+**。** （句點） 來去除這個抽象基底類別的實作。 這會為您產生的屬性和方法。

**實作屬性。** 填寫`FixableDiagnosticIds`屬性的`get`本文中的下列程式碼：

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn 結合診斷及修正藉由比對這些識別項都是字串。 專案範本，產生診斷的識別碼，您可以自由地變更它。 屬性中的程式碼只會傳回自分析器類別的識別碼。

**RegisterCodeFixAsync 方法取得內容。** 內容是很重要，因為程式碼修正可以套用到多個診斷，或在程式碼行上可能有一個以上的問題。 如果您輸入 「 內容 」。 在方法主體中，IntelliSense 完成清單會顯示您一些有用的成員。 沒有 CancellationToken 成員，您可以檢查看看的項目，是否要取消此修正程式。 沒有具有許多實用的成員，並讓您取得的專案和方案的模型物件的文件成員。 範圍的成員開頭，且結尾的程式碼位置可讓您指定當您回報的診斷。

**進行非同步方法。** 您只需要第一件事是修正產生的方法宣告為`async`方法。 不包含抽象類別的實作設定 stub 的程式碼修正`async`關鍵字，即使此方法會傳回`Task`。

**取得語法樹狀結構的根目錄。** 若要修改產生新的語法樹狀結構，以變更所需的程式碼可讓您的程式碼修正。 您需要`Document`從呼叫內容`GetSyntaxRootAsync`。 這是非同步方法，因為有未知的工作，以取得語法樹狀目錄中，可能包括取得檔案從磁碟、 剖析它，以及建置 Roslyn 程式碼模型。 在此期間，使用 Visual Studio UI 中應該有回應`async`啟用。 以下列內容取代方法中的程式碼行：

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**尋找與問題的節點。** 您傳遞內容的範圍內，但您發現可能不是您不必變更程式碼的節點。 回報的診斷僅供範圍 （其中的波浪線所屬） 型別識別項，但您需要將整個物件建立運算式，包括`new`關鍵字開頭和結尾括號。 將下列程式碼新增至您的方法 (並用**Ctrl**+**。** 若要新增`using`陳述式`ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**註冊您的程式碼修正的燈泡 UI。** 當您註冊您的程式碼修正時，Roslyn 外掛到 Visual Studio 燈泡 UI 自動。 使用者會看到他們可以使用**Ctrl**+**。** （句號） 時您分析器波浪線不良`ImmutableArray<T>`建構函式使用。 因為只有當發生問題時，才會執行您的程式碼修正提供者，您可以假設您有您要尋找的物件建立運算式。 從內容參數，您可以註冊新的程式碼修正的結尾新增下列程式碼`RegisterCodeFixAsync`方法：

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

您需要將編輯器插入號放在識別項， `CodeAction`，然後使用**Ctrl**+**。** （句點），將適當`using`這種類型的陳述式。

然後將放在編輯器的插入號`ChangeToImmutableArrayEmpty`識別項，並使用**Ctrl**+**。** 為您產生方法 stub。

這個最後的程式碼片段，您加入註冊的程式碼修正，藉由傳遞`CodeAction`和發現的問題種類的診斷識別碼。 在此範例中，有一個只有此程式碼提供的診斷識別碼的修正程式，讓您可以只將診斷識別碼陣列的第一個元素。 當您建立`CodeAction`，您可以傳入燈泡 UI 應該做的程式碼修正的描述文字。 您也將採用 CancellationToken，並傳回新的文件的函式中傳遞。 新的文件中有新的語法樹狀結構，其中包含您的修補程式碼呼叫`ImmutableArray.Empty`。 此程式碼片段會使用 lambda，讓它可以關閉 objectCreation 節點和內容的文件。

**建構新的語法樹狀結構。** 在 `ChangeToImmutableArrayEmpty`方法，您在稍早所產生的虛設常式的輸入程式碼行： `ImmutableArray<int>.Empty;`。 如果您檢視**語法視覺化檢視**工具視窗同樣地，您可以看到此語法是 SimpleMemberAccessExpression 節點。 這是這個方法需要建構和傳回新的文件中。

第一個變更`ChangeToImmutableArrayEmpty`是新增`async`之前`Task<Document>`因為程式碼產生器不能假設方法應該是非同步。

會填入內容為下列程式碼，使您的方法看起來如下所示：

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

您必須將編輯器插入號放在`SyntaxGenerator`識別項，並使用**Ctrl**+**。** （句點），將適當`using`這種類型的陳述式。

此程式碼使用`SyntaxGenerator`，這是很有用的型別來建構新的程式碼。 取得文件的產生器程式碼問題之後,`ChangeToImmutableArrayEmpty`呼叫`MemberAccessExpression`、 傳遞有我們想要存取的成員的類型和成員的名稱傳遞為字串。

接下來，此方法會擷取的文件根，因為這可能是任意的工作，在一般情況下，等候此呼叫的程式碼，並傳遞取消語彙基元。 Roslyn 程式碼模型為不可變的類似於處理.NET 字串;當您更新字串時，會傳回取得新的字串物件。 當您呼叫`ReplaceNode`，得到新的根節點。 大部分的語法樹狀目錄的共用 （因為它是不可變），但`objectCreation`節點取代`memberAccess` 節點，以及最高到語法樹狀結構根目錄的所有父節點。

## <a name="try-your-code-fix"></a>試用您的程式碼修正

您現在可以按下**F5** Visual Studio 的第二個執行個體中執行您的分析器。 開啟您之前使用的主控台專案。 現在您應該會看到燈泡會出現新的物件建立運算式會為`ImmutableArray<int>`。 如果您按下**Ctrl**+**。** （期間），然後您會看到您的程式碼修正，，，您會看到燈泡 UI 中的自動產生的程式碼差異預覽。 Roslyn 為您建立這。

**Pro 提示：** 如果您啟動 Visual Studio 中，第二個執行個體，而且您沒有看到與您的程式碼修正的燈泡，您可能需要清除 Visual Studio 元件快取。 清除快取會強制 Visual Studio 來重新檢查的元件，因此 Visual Studio 應該會挑選您最新的元件。 首先，請關閉 Visual Studio 的第二個執行個體。 然後，在**Windows 檔案總管**，瀏覽至 *%LOCALAPPDATA%\Microsoft\VisualStudio\15.0Roslyn\\*。 （"15.0"會變更版本與 Visual Studio。） 刪除子目錄*ComponentModelCache*。

## <a name="talk-video-and-finish-code-project"></a>視訊並完成程式碼專案

您可以看到開發，並討論此範例中將進一步[這段演講](https://channel9.msdn.com/events/Build/2015/3-725)。 演講將示範使用分析程式，並引導您完成建置它。

您可以看到所有完成的程式碼[此處](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)。 子資料夾*DoNotUseImmutableArrayCollectionInitializer*並*DoNotUseImmutableArrayCtor*各自找出問題的 C# 檔案和 C# 檔案實作程式碼修正，以顯示在Visual Studio 燈泡 UI。 請注意，完成的程式碼有一些詳細的抽象概念，來避免擷取 ImmutableArray\<T > 一再輸入物件。 它所提供的內容中儲存的型別物件會使用巢狀的已註冊的動作時的子動作 （分析物件的建立和分析集合初始設定） 執行。

## <a name="see-also"></a>另請參閱

* [\\\Build 2015年演講](https://channel9.msdn.com/events/Build/2015/3-725)
* [在 GitHub 上的完整程式碼](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [在 GitHub 上的數個範例分組為三種類型的分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS 網站上的其他文件](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [實作與 GitHub 上的 Roslyn 分析器的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
