---
title: 適用于適用于 immutablearray 的 Roslyn 分析器和程式碼感知程式庫
description: 瞭解如何建立真實世界 Roslyn 分析器，以在使用 system.string NuGet 套件時攔截常見的錯誤。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04b65ae8c81f381ee996da5f20ec15588b9180de
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715765"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>適用于適用于 immutablearray 的 Roslyn 分析器和程式碼感知程式庫

[.NET Compiler Platform](https://github.com/dotnet/roslyn) ( "Roslyn" ) 可協助您建立可感知程式碼的程式庫。 可感知程式碼的程式庫會提供您可以使用的功能，以及 (Roslyn 分析器的工具) 協助您以最佳方式使用程式庫，或避免錯誤。 本主題說明如何建立真實世界 Roslyn 分析器， [以在使用 System.string NuGet 套件](https://www.nuget.org/packages/System.Collections.Immutable) 時攔截常見的錯誤。 此範例也會示範如何針對分析器所找到的程式碼問題，提供程式碼修正程式。 使用者會在 Visual Studio 燈泡 UI 中看到程式碼修正，並且可以自動套用程式碼的修正程式。

## <a name="get-started"></a>開始使用

您需要下列各項才能建立此範例：

* Visual Studio 2015 (不是 Express Edition) 或更新版本。 您可以使用免費的 [Visual Studio Community 版](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 您也可以在安裝 Visual Studio 時，檢查 [**一般工具**] 底下的 **Visual Studio 擴充性工具**，同時安裝 SDK。 如果您已經安裝 Visual Studio，也可以移至 **主要功能表檔**[  >  **新增**  >  **專案**]，在左側流覽窗格中選擇 **[** **c #** ]，然後選擇 [擴充性]，來安裝此 SDK。 當您選擇 [**安裝 Visual Studio 擴充性工具**] 階層連結專案範本時，它會提示您下載並安裝 SDK。
* [.NET Compiler Platform ( "Roslyn" ) SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK)。 您也可以安裝此 SDK，方法是移至主要 **功能表檔** 的 [  >  **新增**  >  **專案**]，在左側流覽窗格中選擇 [  **c #** ]，然後選擇 [擴充性]。 當您選擇 [**下載 .NET COMPILER PLATFORM sdk**] 階層連結專案範本時，它會提示您下載並安裝 sdk。 此 SDK 包含 [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Syntax-Visualizer.md)。 這項實用的工具可協助您找出您應該在分析器中尋找的程式碼模型類型。 分析器基礎結構會針對特定程式碼模型類型呼叫您的程式碼，因此您的程式碼只會在必要時執行，而且只能專注于分析相關的程式碼。

## <a name="whats-the-problem"></a>怎麼了？

假設您提供具有 ImmutableArray (的程式庫，例如 <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) 支援。 C # 開發人員對 .NET 陣列有許多體驗。 不過，由於實作為適用于 immutablearray 和優化技術的本質，因此 c # 開發人員觀念會導致您程式庫的使用者撰寫中斷的程式碼，如下所述。 此外，在執行時間之前，使用者不會看到他們的錯誤，這並不是在使用 .NET Visual Studio 的品質體驗。

使用者熟悉撰寫如下的程式碼：

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

C # 開發人員很熟悉如何建立空陣列以填入後續的程式程式碼，以及使用集合初始化運算式語法。 不過，在執行時間針對 ImmutableArray 損毀撰寫相同的程式碼：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

第一個錯誤是因為 ImmutableArray 實行使用結構來包裝基礎資料儲存體。 結構必須具有無參數的函式，以便 `default(T)` 運算式可以傳回所有零或 null 成員的結構。 當程式碼存取時 `b1.Length` ，會有執行時間 null 取值錯誤，因為 ImmutableArray 結構中沒有基礎儲存陣列。 建立空白 ImmutableArray 的正確方式是 `ImmutableArray<int>.Empty` 。

集合初始化運算式的錯誤發生的原因是，方法會在 `ImmutableArray.Add` 每次呼叫時傳回新的實例。 由於適用于 immutablearray 不會變更，因此當您新增新的專案時，您會收到新的 ImmutableArray 物件 (因為先前現有的 ImmutableArray) ，因此可能會共用儲存體。 因為在 `b2` 呼叫五次之前指向第一個 ImmutableArray `Add()` ， `b2` 是預設 ImmutableArray。 在其上呼叫長度也會因為 null 取值錯誤而損毀。 將 ImmutableArray 初始化而不需要手動呼叫 Add 的正確方式是使用 `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` 。

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>尋找相關的語法節點類型來觸發您的分析器

 若要開始建立分析器，請先找出您需要尋找何種類型的 SyntaxNode。 從功能表 **視圖** 的 [   >  **其他 Windows**  >  **Roslyn] Syntax Visualizer** 啟動 Syntax Visualizer。

將編輯器的插入號放在宣告的行上 `b1` 。 您會看到 Syntax Visualizer 顯示在 `LocalDeclarationStatement` 語法樹狀結構的節點中。 此節點具有，後者接著具有， `VariableDeclaration` `VariableDeclarator` `EqualsValueClause` 而最後會有一個 `ObjectCreationExpression` 。 當您在節點的 Syntax Visualizer 樹狀結構中按一下時，編輯器視窗中的語法會反白顯示，以顯示該節點所代表的程式碼。 SyntaxNode 子類型的名稱符合 c # 文法中使用的名稱。

## <a name="create-the-analyzer-project"></a>建立分析器專案

從主功能表選擇 [檔案  >  **新增**  >  **專案**]。 在 [ **新增專案** ] 對話方塊中，于左側導覽列中的 [ **c #** 專案] 下 **選擇 [擴充** 性]，然後在右窗格中選擇 [ **具有程式碼修正的分析器** ] 專案範本。 輸入名稱，並確認對話方塊。

範本會開啟 *DiagnosticAnalyzer.cs* 檔案。 選擇 [編輯器緩衝區] 索引標籤。這個檔案的分析器類別 (由您提供的專案) 衍生自 `DiagnosticAnalyzer` (ROSLYN API 類型) 的名稱所組成。 您的新類別 `DiagnosticAnalyzerAttribute` 會宣告您的分析器與 c # 語言相關，以便編譯器探索和載入您的分析器。

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

您可以使用以 c # 程式碼為目標的 Visual Basic 來執行分析器，反之亦然。 在 DiagnosticAnalyzerAttribute 中，選擇您的分析器以一種或兩種語言為目標，是比較重要的。 需要詳細模型化語言的更精密分析器只能以單一語言為目標。 例如，如果您的分析器只會檢查類型名稱或公用成員名稱，則可能會在 Visual Basic 和 c # 中使用通用語言模型 Roslyn 提供。 例如，FxCop 會警告某個類別所 <xref:System.Runtime.Serialization.ISerializable> 執行，但該類別沒有與 <xref:System.SerializableAttribute> 語言無關的屬性，而且適用于 Visual Basic 和 c # 程式碼。

## <a name="initialize-the-analyzer"></a>初始化分析器

 在類別中向下移動一點 `DiagnosticAnalyzer` ，以查看 `Initialize` 方法。 編譯器會在啟用分析器時呼叫這個方法。 方法會使用 `AnalysisContext` 物件，讓您的分析器取得內容資訊，並針對您想要分析的程式碼種類註冊回呼。

```csharp
public override void Initialize(AnalysisContext context) {}
```

在此方法中開啟新行，然後輸入 "coNtext"。 以查看 IntelliSense 完成清單。 您可以在完成清單中看到，有許多 `Register...` 方法可以處理各種類型的事件。 例如，第一個 `RegisterCodeBlockAction` 會呼叫回您的程式碼，以取得區塊，通常是在大括弧之間的程式碼。 註冊區塊也會回呼至您的程式碼，以取得欄位的初始化運算式、提供給屬性的值，或選擇性參數的值。

另一個範例是，在 `RegisterCompilationStartAction` 編譯開始時呼叫回您的程式碼，當您需要在許多位置上收集狀態時，這非常有用。 您可以建立資料結構，比方說，若要收集所有使用的符號，並在每次呼叫分析器來取得某些語法或符號，您可以儲存資料結構中每個位置的相關資訊。 當您因為編譯結束而被呼叫後，您可以分析您儲存的所有位置，例如，從每個語句報告程式碼所使用的符號 `using` 。

使用 **Syntax Visualizer**，您已瞭解您想要在編譯器處理 ObjectCreationExpression 時呼叫。 您可以使用此程式碼來設定回呼：

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

您會註冊一個語法節點，並只篩選物件建立語法節點。 依照慣例，分析器作者在註冊動作時會使用 lambda，這有助於讓分析器保持無狀態。 您可以使用 **從使用方式產生** 的 Visual Studio 功能來建立 `AnalyzeObjectCreation` 方法。 這樣也會為您產生正確類型的內容參數。

## <a name="set-properties-for-users-of-your-analyzer"></a>設定您分析器使用者的屬性

為了讓您的分析器適當地顯示在 Visual Studio UI 中，請尋找並修改下列程式程式碼，以識別您的分析器：

```csharp
internal const string Category = "Naming";
```

將 `"Naming"` 變更為 `"API Guidance"`。

接下來，使用 **方案總管** 尋找並開啟專案中的 *.resources 檔案。* 您可以針對分析器、標題等放入描述。您現在可以將所有這些值的值變更為 `"Don't use ImmutableArray<T> constructor"` 。 您可以在字串中放入字串格式引數 ({0} 、等等 {1} ) ，而且稍後當您呼叫時 `Diagnostic.Create()` ，可以提供 `params` 要傳遞的引數陣列。

## <a name="analyze-an-object-creation-expression"></a>分析物件建立運算式

`AnalyzeObjectCreation`方法會採用程式碼分析器架構所提供的不同類型內容。 `Initialize`方法的可 `AnalysisContext` 讓您註冊動作回呼，以設定您的分析器。 `SyntaxNodeAnalysisContext`例如，具有 `CancellationToken` 可供您傳遞的。 如果使用者在編輯器中開始輸入，Roslyn 會取消執行中的分析器以儲存工作並改善效能。 另一個範例是，此內容具有會傳回物件建立語法節點的 Node 屬性。

取得節點，您可以假設它是您篩選語法節點動作的類型：

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>第一次使用您的分析器啟動 Visual Studio

藉由建立及執行您的分析器來啟動 Visual Studio (按 **F5**) 。 由於 **方案總管** 中的啟始專案是 VSIX 專案，因此執行您的程式碼會建立您的程式碼和 vsix，然後啟動已安裝該 vsix 的 Visual Studio。 當您以這種方式啟動 Visual Studio 時，會以不同的登錄區啟動，讓您在建立分析器時，您的測試實例不會影響 Visual Studio 的主要用途。 當您第一次啟動時，Visual Studio 會進行數個初始化，類似于您在安裝後第一次啟動 Visual Studio。

建立主控台專案，然後在主控台應用程式的主要方法中輸入陣列程式碼：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

的程式程式碼 `ImmutableArray` 具有波浪線，因為您需要取得不可變的 NuGet 套件，並將 `using` 語句新增至您的程式碼。 在 **方案總管** 的專案節點上按右指標按鈕，然後選擇 [ **管理 NuGet 套件**]。 在 [NuGet 管理員] 中，于 [搜尋] 方塊中輸入「不可變的」，然後選擇 **[ (]** ，不要選擇左窗格中的 **[) ]** ，然後按右窗格中的 [ **安裝** ] 按鈕。 安裝套件會將參考加入至您的專案參考。

您仍然會在底下看到紅色波浪線 `ImmutableArray` ，所以請將插入號放在該識別碼中，然後按下 **Ctrl** + **。**  (期間) 以顯示建議的修正功能表，並選擇新增適當的 `using` 語句。

**全部儲存並關閉** Visual Studio 的第二個實例，讓您進入乾淨狀態以繼續。

## <a name="finish-the-analyzer-using-edit-and-continue"></a>使用 [編輯後繼續] 完成分析器

在 Visual Studio 的第一個實例中，在方法的開頭設定中斷點， `AnalyzeObjectCreation` 方法是在第一行的插入點按 **F9** 。

使用 **F5** 再次啟動您的分析器，然後在 Visual Studio 的第二個實例中，重新開啟您上次建立的主控台應用程式。

您會在中斷點返回 Visual Studio 的第一個實例，因為 Roslyn 編譯器會看到物件建立運算式，並將它呼叫至您的分析器。

**取得物件建立節點。** `objectCreation`按 **F10** 鍵，然後在 [即時運算 **] 視窗** 中評估運算式，以逐步執行設定變數的程式列 `"objectCreation.ToString()"` 。 您會看到變數所指向的語法節點，就是程式碼 `"new ImmutableArray<int>()"` ，就是您要尋找的內容。

**取得 ImmutableArray<T \> 類型物件。** 您需要檢查所建立的類型是否為 ImmutableArray。 首先，您會取得代表此類型的物件。 您可以使用語義模型檢查型別，以確保您有正確的型別，而且您不會比較中的字串 `ToString()` 。 在函式的結尾輸入下列程式程式碼：

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

您可以使用倒引號 (') 和泛型參數的數目，在中繼資料中指定泛型型別。 這就是為什麼您看不到「.。。\<T>中繼資料名稱中的 ImmutableArray」。

此語義模型有許多有用的專案，可讓您詢問有關符號、資料流程、變數存留期等問題。Roslyn 會將語法節點與語義模型分開，以因應各種不同的工程理由 (效能、模型化錯誤程式碼等 ) 。 您希望編譯模型查閱參考中包含的資訊，以進行精確的比較。

您可以將黃色執行指標拖曳到編輯器視窗的左側。 將它拖曳至設定變數的程式程式碼， `objectCreation` 並使用 **F10** 不進入新的程式程式碼。 如果您將滑鼠指標暫留在變數上 `immutableArrayOfType` ，您會看到在語義模型中找到確切的型別。

**取得物件建立運算式的類型。** 在本文中，有幾種方式可使用「類型」，但這表示如果您有「新的 Foo」運算式，您需要取得 Foo 的模型。 您需要取得物件建立運算式的類型，以查看它是否為 ImmutableArray \<T> 類型。 再次使用語義模型，在物件建立運算式中取得類型符號 (ImmutableArray) 的符號資訊。 在函式的結尾輸入下列程式程式碼：

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

因為您的分析器需要在編輯器緩衝區中處理不完整或不正確的程式碼 (例如，有遺漏的 `using` 語句) ，您應該檢查是否有 `symbolInfo` `null` 。 您必須從符號資訊物件取得命名類型 (INamedTypeSymbol) ，才能完成分析。

**比較類型。** 由於有一種開放式泛型型別的 T 是我們要尋找的，而程式碼中的型別是具象的泛型型別，因此您可以從 (開放式泛型) 型別來查詢型別所構成的符號資訊，然後再與結果比較 `immutableArrayOfTType` 。 在方法的結尾輸入下列內容：

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**報告診斷。** 報告診斷非常簡單。 您可以使用在專案範本中為您建立的規則（在 Initialize 方法之前定義的）。 由於程式碼中的這種情況是錯誤的，您可以變更已初始化規則的行，以 `DiagnosticSeverity.Warning` (紅色波浪線) 來取代 (綠色曲線) `DiagnosticSeverity.Error` 。 規則的其餘部分會從您在逐步解說開頭附近編輯的資源中初始化。 您也需要報告波浪線的位置，也就是物件建立運算式類型規格的位置。 在區塊中輸入下列程式碼 `if` ：

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

您的函式看起來應該像這樣 (可能會以不同的格式) ：

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

移除中斷點，讓您可以看到您的分析器工作 (，並停止返回 Visual Studio) 的第一個實例。 將執行指標拖曳至方法的開頭，然後按下 **F5** 以繼續執行。 當您切換回 Visual Studio 的第二個實例時，編譯器將會開始再次檢查程式碼，而它會呼叫您的分析器。 您可以在下方看到波浪線 `ImmutableType<int>` 。

## <a name="adding-a-code-fix-for-the-code-issue"></a>新增程式碼問題的「程式碼修正」

開始之前，請先關閉 Visual Studio 的第二個實例，然後在您要開發分析器) Visual Studio (的第一個實例中停止偵錯工具。

**新增類別。** 在 **方案總管** 的專案節點上，使用快捷方式功能表 (右指標按鈕) ，然後加入宣告新專案。 加入名為的類別 `BuildCodeFixProvider` 。 此類別必須衍生自 `CodeFixProvider` ，而且您必須使用 **Ctrl** + **。**  (期間) ，以叫用加入正確語句的程式碼修正 `using` 。 這個類別也需要以 `ExportCodeFixProvider` 屬性標注，而且您必須加入 `using` 語句來解析 `LanguageNames` 列舉。 您應該會有一個類別檔案，其中包含下列程式碼：

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**存根衍生的成員。** 現在，將編輯器的插入號放在識別碼中， `CodeFixProvider` 然後按下 **Ctrl** + **。**  (期間) 以將這個抽象基類的實作為存根。 這會為您產生屬性和方法。

**執行屬性。** `FixableDiagnosticIds`使用下列程式碼填入屬性的 `get` 主體：

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn 藉由比對這些識別碼（只是字串）來整合診斷和修正程式。 專案範本為您產生了診斷識別碼，而且您可以隨意變更它。 屬性中的程式碼只會傳回分析器類別的識別碼。

**RegisterCodeFixAsync 方法會接受內容。** 內容很重要，因為程式碼修正可以套用至多個診斷，或是一行程式碼可能有一個以上的問題。 如果您輸入「內容」。 在方法的主體中，IntelliSense 完成清單會顯示一些有用的成員。 您可以查看 CancellationToken 成員，看看是否有任何要取消修正的問題。 有一個檔成員有許多有用的成員，可讓您取得專案和方案模型物件。 範圍成員是在您回報診斷時所指定之程式碼位置的開頭和結尾。

**將方法設為非同步。** 您必須做的第一件事，就是將產生的方法宣告修正為 `async` 方法。 設定象抽象類別的程式碼修正不會包含 `async` 關鍵字，即使方法傳回也一樣 `Task` 。

**取得語法樹狀結構的根目錄。** 若要修改程式碼，您必須使用程式碼修正所做的變更來產生新的語法樹狀結構。 您需要 `Document` 來自內容的才能呼叫 `GetSyntaxRootAsync` 。 這是非同步方法，因為取得語法樹狀結構有未知的工作，可能包括從磁片取得檔案、剖析它，以及為它建立 Roslyn 程式碼模型。 在這段期間，Visual Studio UI 應該會有回應，這會使用 `async` 啟用。 以下列程式碼取代方法中的程式程式碼：

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**找出有問題的節點。** 您會傳入內容約制，但您發現的節點可能不是您必須變更的程式碼。 報告的診斷只提供類型識別碼的範圍 (其中的波浪線所屬) ，但您需要取代整個物件建立運算式，包括 `new` 開頭的關鍵字和結尾的括弧。 將下列程式碼新增至您的方法 (並使用 **Ctrl** + **。** 若要加入 `using`) 的語句 `ObjectCreationExpressionSyntax` ：

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**註冊適用于燈泡 UI 的程式碼修正。** 當您註冊程式碼修正程式時，Roslyn 會自動插入 Visual Studio 燈泡 UI 中。 終端使用者會看到他們可以使用 **Ctrl** + **。** 當您的分析器波浪線不正確的函式時，)  (期間 `ImmutableArray<T>` 。 因為您的程式碼修正提供者只會在發生問題時執行，所以您可以假設您有要尋找的物件建立運算式。 從內容參數，您可以將下列程式碼加入至方法的結尾，以註冊新的程式碼修正 `RegisterCodeFixAsync` ：

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

您必須將編輯器的插入號放在識別碼中， `CodeAction` 然後使用 **Ctrl** + **。**  (期間) 加入 `using` 此類型的適當語句。

然後將編輯器的插入號放在 `ChangeToImmutableArrayEmpty` 識別碼中，然後使用 **Ctrl** + **。** 再次為您產生這個方法 stub。

您新增的最後一個程式碼片段會藉由傳遞所 `CodeAction` 找到的問題種類的和診斷識別碼，來註冊程式碼修正。 在此範例中，只有一個診斷識別碼可供此程式碼提供修正程式，因此您可以直接傳遞診斷識別碼陣列的第一個元素。 當您建立時 `CodeAction` ，會傳入燈泡 UI 應用來作為程式碼修正描述的文字。 您也可以傳入接受 CancellationToken 的函式，並傳回新的檔。 新檔有一個新的語法樹狀結構，其中包含您所呼叫的修補程式碼 `ImmutableArray.Empty` 。 此程式碼片段會使用 lambda，讓它可以在 objectCreation 節點和內容檔上關閉。

**建立新的語法樹狀結構。** 在 `ChangeToImmutableArrayEmpty` 您稍早產生其存根的方法中，輸入程式程式碼： `ImmutableArray<int>.Empty;` 。 如果您再次查看 [ **Syntax Visualizer** ] 工具視窗，您可以看到此語法為 SimpleMemberAccessExpression 節點。 這就是這個方法需要在新檔中建立和傳回的內容。

的第一項變更 `ChangeToImmutableArrayEmpty` 是要 `async` 在之前加入，因為程式碼產生器 `Task<Document>` 無法假設方法應該是非同步。

使用下列程式碼填入主體，讓您的方法看起來像下面這樣：

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

您必須將編輯器的插入號放在識別碼中 `SyntaxGenerator` ，並使用 **Ctrl** + **。**  (期間) 加入 `using` 此類型的適當語句。

此程式碼 `SyntaxGenerator` 會使用，這是用來建立新程式碼的實用型別。 取得具有程式碼問題的檔產生器之後， `ChangeToImmutableArrayEmpty` 呼叫 `MemberAccessExpression` ，傳遞具有要存取之成員的型別，並以字串形式傳遞成員的名稱。

接下來，此方法會提取檔的根目錄，因為這可能會在一般情況下涉及任意的工作，所以程式碼會等候此呼叫並傳遞解除標記。 Roslyn 程式碼模型是不可變的，例如使用 .NET 字串;當您更新字串時，會取得傳回的新字串物件。 當您呼叫時 `ReplaceNode` ，會取回新的根節點。 大部分的語法樹狀結構都是 (的，因為它是不可變的) ，但節點 `objectCreation` 會取代節點 `memberAccess` ，以及所有父節點（最多到語法樹狀結構根目錄）。

## <a name="try-your-code-fix"></a>試用您的程式碼修正

您現在可以按 **F5** ，在 Visual Studio 的第二個實例中執行分析器。 開啟您先前使用的主控台專案。 現在您應該會看到燈泡出現在新的物件建立運算式的位置 `ImmutableArray<int>` 。 如果您按下 **Ctrl** + **。**  (期間) ，您將會看到您的程式碼修正，且您會在燈泡 UI 中看到自動產生的程式碼差異預覽。 Roslyn 會為您建立此程式。

**Pro 提示：** 如果您啟動 Visual Studio 的第二個實例，而且沒有看到程式碼修正的燈泡，您可能需要清除 Visual Studio 元件快取。 清除快取會強制 Visual Studio 重新檢查元件，因此 Visual Studio 接著應挑選最新的元件。 首先，關閉 Visual Studio 的第二個實例。 然後，在 **Windows 檔案總管** 中，流覽 *至 \\ %LOCALAPPDATA%\Microsoft\VisualStudio\16.0Roslyn*。  ("16.0" 從版本變更為具有 Visual Studio 的版本。 ) 刪除子目錄 *ComponentModelCache*。

## <a name="talk-video-and-finish-code-project"></a>討論影片和完成程式碼專案

您可以在 [此討論](https://channel9.msdn.com/events/Build/2015/3-725)中看到此範例的開發和討論。 這段演講將示範可運作的分析器，並逐步引導您進行建立。

您可以在 [這裡](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)看到所有完成的程式碼。 *DoNotUseImmutableArrayCollectionInitializer* 和 *DoNotUseImmutableArrayCtor* 的子資料夾都有一個 c # 檔案，可用於尋找問題和一個 c # 檔案，該檔案會執行顯示在 Visual Studio 燈泡 UI 中的程式碼修正程式。 請注意，完成的程式碼有更多的抽象概念，可避免過度提取 ImmutableArray \<T> 型別物件。 它會使用嵌套註冊的動作，將類型物件儲存在可使用的內容中，只要子動作 (分析物件建立，並分析) 執行的集合初始化。

## <a name="see-also"></a>請參閱

* [\\\Build 2015 談](https://channel9.msdn.com/events/Build/2015/3-725)
* [GitHub 上已完成的程式碼](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [GitHub 上的數個範例，分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS 網站上的其他檔](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [在 GitHub 上以 Roslyn 分析器執行的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
