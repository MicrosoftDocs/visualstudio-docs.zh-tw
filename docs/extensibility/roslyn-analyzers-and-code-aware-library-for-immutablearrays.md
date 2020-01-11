---
title: 適用于適用于 immutablearray 的 Roslyn 分析器和程式碼感知程式庫 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8665a37e4afd387ff4f77a8bdb5da430d773ae1d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848724"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>適用于適用于 immutablearray 的 Roslyn 分析器和程式碼感知程式庫

[.NET Compiler Platform](https://github.com/dotnet/roslyn) （"Roslyn"）可協助您建立程式碼感知程式庫。 程式碼感知程式庫提供您可以使用的功能和工具（Roslyn 分析器），協助您以最佳方式使用程式庫，或避免發生錯誤。 本主題說明如何建立真實世界的 Roslyn 分析器，以在使用[system.object](https://www.nuget.org/packages/System.Collections.Immutable)的 NuGet 套件時攔截常見的錯誤。 此範例也會示範如何為分析器所找到的程式碼問題提供代碼解析。 使用者會在 Visual Studio 燈泡 UI 中看到程式碼修正，並可自動套用程式碼的修正。

## <a name="get-started"></a>開始使用

若要建立此範例，您需要下列各項：

* Visual Studio 2015 （非 Express Edition）或更新版本。 您可以使用免費的[Visual Studio Community 版本](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 您也可以在安裝 Visual Studio 時，檢查 [**一般工具**] 底下的**Visual Studio 擴充性工具**以同時安裝 SDK。 如果您已安裝 Visual Studio，您也可以前往**主功能表檔案** > **新增** > **專案**，在左側流覽窗格中選擇**C#** ，然後**選擇 擴充**性，來安裝此 SDK。 當您選擇 [**安裝 Visual Studio 擴充性工具**] 階層連結專案範本時，它會提示您下載並安裝 SDK。
* [.NET Compiler Platform （"Roslyn"） SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK)。 若要安裝此 SDK，請移**至 > ** **新** > **專案**的主功能表檔案，在**C#** 左側流覽窗格中選擇，然後**選擇 [擴充性]。** 當您選擇 [**下載 .NET COMPILER PLATFORM SDK**] 階層連結專案範本時，它會提示您下載並安裝 SDK。 此 SDK 包含[Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)。 這項實用的工具可協助您找出您在分析器中應該尋找的程式碼模型類型。 分析器基礎結構會針對特定的程式碼模型類型呼叫您的程式碼，因此您的程式碼只會在必要時執行，而且只能著重于分析相關的程式碼。

## <a name="whats-the-problem"></a>怎麼了？

假設您提供具有 ImmutableArray （例如 <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>）支援的程式庫。 C#開發人員有許多 .NET 陣列的經驗。 不過，由於執行中使用的適用于 immutablearray 和優化技術本質， C#開發人員觀念會使您的程式庫使用者撰寫中斷的程式碼，如下所述。 此外，在執行時間之前，使用者不會看到其錯誤，這不是用來在 .NET 中 Visual Studio 的品質經驗。

使用者熟悉撰寫如下所示的程式碼：

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

建立空陣列以填入後續的程式程式碼，並使用集合初始化運算式語法，對C#開發人員而言是很熟悉的。 不過，針對 ImmutableArray 撰寫相同的程式碼會在執行時間損毀：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

第一個錯誤是因為 ImmutableArray 實行使用結構來包裝基礎資料存放區。 結構必須具有無參數的函式，如此 `default(T)` 運算式才能傳回具有所有零或 null 成員的結構。 當程式碼存取 `b1.Length`時，會發生執行時間 null 取值錯誤，因為 ImmutableArray 結構中沒有基礎儲存陣列。 建立空白 ImmutableArray 的正確方式是 `ImmutableArray<int>.Empty`。

因為 `ImmutableArray.Add` 方法會在每次呼叫時傳回新的實例，所以會發生集合初始化運算式的錯誤。 由於適用于 immutablearray 永遠不會變更，因此當您新增新的專案時，您會收到新的 ImmutableArray 物件（基於效能考慮，先前現有的 ImmutableArray 可能會共用儲存區）。 因為 `b2` 會指向第一個 ImmutableArray，然後再呼叫 `Add()` 五次，所以 `b2` 是預設的 ImmutableArray。 在它上呼叫長度也會因為 null 取值錯誤而當機。 將 ImmutableArray 初始化而不手動呼叫 Add 的正確方式，是使用 `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`。

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>尋找相關的語法節點類型來觸發您的分析器

 若要開始建立分析器，請先找出您需要尋找的 SyntaxNode 類型。 從 > **其他 Windows** > **Roslyn Syntax Visualizer**的功能表**視圖**啟動**Syntax Visualizer** 。

將編輯器的插入號放在宣告 `b1`的那一行。 您會看到 Syntax Visualizer 顯示在語法樹狀結構的 [`LocalDeclarationStatement`] 節點中。 這個節點具有 `VariableDeclaration`，而它又有一個 `VariableDeclarator`，而它又有一個 `EqualsValueClause`，最後還有一個 `ObjectCreationExpression`。 當您在節點的 Syntax Visualizer 樹狀目錄中按一下時，[編輯器] 視窗中的語法會反白顯示該節點所代表的程式碼。 SyntaxNode 子類型的名稱符合C#文法中使用的名稱。

## <a name="create-the-analyzer-project"></a>建立分析器專案

從主功能表中 **，選擇 [** 檔案] > [**新增** > **專案**]。 在 [**新增專案**] 對話方塊中**C#** ，于左側導覽列的 [專案] 底下 **，選擇 [** 擴充性]，然後在右窗格中選擇 [**具有程式碼修正的分析器**] 專案範本。 輸入名稱並確認對話方塊。

此範本會開啟*DiagnosticAnalyzer.cs*檔案。 選擇編輯器 [緩衝區] 索引標籤。此檔案具有從 `DiagnosticAnalyzer` （Roslyn API 類型）衍生的分析器類別（由您提供專案的名稱所組成）。 您的新類別有 `DiagnosticAnalyzerAttribute` 宣告您的C#分析器與語言相關，因此編譯器會探索並載入您的分析器。

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

您可以使用以程式碼為目標C#的 Visual Basic 來執行分析器，反之亦然。 在 DiagnosticAnalyzerAttribute 中，選擇您的分析器是以一種語言或兩者為目標，是比較重要的。 需要語言的詳細模型化的更複雜分析器只能以單一語言為目標。 例如，如果您的分析器只會檢查類型名稱或公用成員名稱，則可能會在 Visual Basic 和C#上使用通用語言模型 Roslyn 供應專案。 例如，FxCop 會警告某個類別會執行 <xref:System.Runtime.Serialization.ISerializable>，但類別沒有與語言無關的 <xref:System.SerializableAttribute> 屬性，而且適用于 Visual Basic 和C#程式碼。

## <a name="initialize-the-analyzer"></a>初始化分析器

 在 `DiagnosticAnalyzer` 類別中向下一小部分，查看 `Initialize` 方法。 編譯器會在啟用分析器時呼叫這個方法。 方法會採用 `AnalysisContext` 物件，讓您的分析器取得內容資訊，並針對您想要分析的程式碼類型註冊事件的回呼。

```csharp
public override void Initialize(AnalysisContext context) {}
```

在此方法中開啟新的一行，並輸入「內容」。 以查看 IntelliSense 完成清單。 您可以在完成清單中看到有許多 `Register...` 方法可以處理各種類型的事件。 例如，第一個 `RegisterCodeBlockAction`，會呼叫區塊的程式碼，這通常會在大括弧之間進行程式碼。 針對某個區塊註冊，也會回呼您的程式碼，以取得欄位的初始化運算式、提供給屬性的值，或選擇性參數的值。

另一個範例是 `RegisterCompilationStartAction`，在編譯開始時回呼您的程式碼，當您需要收集許多位置的狀態時，這會很有用。 您可以建立資料結構（例如）來收集所有使用的符號，而且每次重新呼叫您的分析器以取得某種語法或符號時，您都可以儲存資料結構中每個位置的相關資訊。 當您因為編譯結束而呼叫回來時，可以分析您儲存的所有位置，例如，從每個 `using` 語句報告程式碼所使用的符號。

使用**Syntax Visualizer**，您已瞭解您想要在編譯器處理 ObjectCreationExpression 時呼叫。 您可以使用下列程式碼來設定回呼：

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

您會註冊語法節點，並僅針對物件建立語法節點進行篩選。 依照慣例，分析器作者會在註冊動作時使用 lambda，這有助於讓分析器保持無狀態。 您可以使用**從使用量產生**的 Visual Studio 功能來建立 `AnalyzeObjectCreation` 方法。 這也會為您產生正確類型的內容參數。

## <a name="set-properties-for-users-of-your-analyzer"></a>設定分析器使用者的屬性

為了讓您的分析器適當地在 Visual Studio UI 中顯示，請尋找並修改下列程式程式碼，以識別您的分析器：

```csharp
internal const string Category = "Naming";
```

將 `"Naming"` 變更為 `"API Guidance"`。

接下來，使用**方案總管**尋找並開啟專案中的*Resources .resx*檔案。 您可以在分析器、標題等專案中放入描述。您現在可以將所有這些值都變更為 `"Don't use ImmutableArray<T> constructor"`。 您可以將字串格式引數放在字串中（{0}、{1}等），稍後當您呼叫 `Diagnostic.Create()`時，可以提供要傳遞之引數的 `params` 陣列。

## <a name="analyze-an-object-creation-expression"></a>分析物件建立運算式

`AnalyzeObjectCreation` 方法會採用程式碼分析器架構所提供的不同類型內容。 `Initialize` 方法的 `AnalysisContext` 可讓您註冊動作回呼來設定您的分析器。 例如，`SyntaxNodeAnalysisContext`有一個可供您傳遞的 `CancellationToken`。 如果使用者開始在編輯器中輸入，Roslyn 會取消執行分析器以儲存工作並改善效能。 另一個範例是，這個內容有一個節點屬性，它會傳回物件建立語法節點。

取得節點，您可以假設這是您用來篩選語法節點動作的類型：

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>第一次啟動分析器的 Visual Studio

建立並執行您的分析器以啟動 Visual Studio （按**F5**）。 由於**方案總管**中的啟始專案是 VSIX 專案，因此執行您的程式碼會建立您的程式碼和 vsix，然後啟動已安裝該 vsix 的 Visual Studio。 當您以這種方式啟動 Visual Studio 時，它會以不同的登錄 hive 啟動，如此您在建立分析器時，您的測試實例就不會影響 Visual Studio 的主要使用。 當您第一次以這種方式啟動時，Visual Studio 會執行數個初始化，類似于您在安裝後第一次啟動 Visual Studio。

建立主控台專案，然後在主控台應用程式的 Main 方法中輸入陣列代碼：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

具有 `ImmutableArray` 的程式程式碼具有波浪線，因為您需要取得不可變的 NuGet 套件，並將 `using` 語句加入至您的程式碼。 在**方案總管**的專案節點上按右指標按鈕，然後選擇 [**管理 NuGet 封裝**]。 在 NuGet 管理員中，于搜尋方塊中輸入「固定」，然後在左窗格中選擇 [專案] [ **system.object** ] （**請勿選擇 [不變]** ），然後按右窗格中的 [**安裝**] 按鈕。 安裝套件會將參考新增至您的專案參考。

您仍然會在 [`ImmutableArray`] 底下看到紅色波浪線，因此請將插入點放在該識別碼中，然後按**Ctrl**+ **。** （期間）以顯示建議的修正功能表，並選擇新增適當的 `using` 語句。

**全部儲存並關閉**Visual Studio 的第二個實例，以讓您進入乾淨狀態以繼續進行。

## <a name="finish-the-analyzer-using-edit-and-continue"></a>使用 [編輯後繼續] 完成分析器

在第一個 Visual Studio 實例中，請在第一行的插入號上按**F9** ，以在 `AnalyzeObjectCreation` 方法的開頭設定中斷點。

使用**F5**再次啟動您的分析器，然後在 Visual Studio 的第二個實例中，重新開啟您上次建立的主控台應用程式。

您會回到中斷點的第一個 Visual Studio 實例，因為 Roslyn 編譯器會看到物件建立運算式，並呼叫您的分析器。

**取得物件建立節點。** 按下**F10**鍵不進入設定 `objectCreation` 變數的那一行，然後在 [即時運算 **] 視窗**中評估運算式 `"objectCreation.ToString()"`。 您會看到變數所指向的語法節點是程式碼 `"new ImmutableArray<int>()"`，只是您要尋找的內容。

**取得 ImmutableArray < T\> 類型物件。** 您需要檢查所建立的類型是否為 ImmutableArray。 首先，您會取得代表這個類型的物件。 您可以使用語義模型檢查類型，以確保您擁有正確的類型，而且不會比較 `ToString()`的字串。 在函式的結尾輸入下列程式程式碼：

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

您可以使用倒引號（'）和泛型參數的數目，在中繼資料中指定泛型型別。 這就是為什麼您看不到「.。。中繼資料名稱中的 ImmutableArray\<T > "。

此語義模型有許多有用的專案，可讓您詢問有關符號、資料流程、變數存留期等等的問題。Roslyn 會根據各種工程原因（效能、模型錯誤程式碼等），將語法節點與語義模型分開。 您想要讓編譯模型查閱參考中包含的資訊，以進行精確的比較。

您可以將黃色執行指標拖曳至編輯器視窗的左側。 將它拖曳到設定 `objectCreation` 變數的那一行，並使用**F10**逐步執行您的新程式程式碼。 如果您將滑鼠指標暫留在變數 `immutableArrayOfType`上，就會看到我們在語義模型中找到正確的類型。

**取得物件建立運算式的類型。** 在本文的幾個方法中，會使用「類型」，但這表示如果您有「新的 Foo」運算式，則需要取得 Foo 的模型。 您需要取得物件建立運算式的類型，以查看它是否為 ImmutableArray\<T > 類型。 再次使用語義模型，以取得物件建立運算式中類型符號（ImmutableArray）的符號資訊。 在函式的結尾輸入下列程式程式碼：

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

因為您的分析器需要在編輯器緩衝區中處理不完整或不正確的程式碼（例如，遺漏 `using` 語句），所以您應該檢查是否有 `null`的 `symbolInfo`。 您必須從符號資訊物件取得命名類型（INamedTypeSymbol），才能完成分析。

**比較類型。** 因為我們要尋找的是開放式泛型型別的 T，而程式碼中的類型是具象的泛型型別，所以您可以從（開放式泛型型別）來查詢類型的符號資訊，並將該結果與 `immutableArrayOfTType`比較。 在方法的結尾輸入下列內容：

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**報告診斷。** 報告診斷非常簡單。 您會在專案範本中使用為您建立的規則，其定義于 Initialize 方法之前。 由於程式碼中的這種情況是錯誤，因此您可以變更已初始化規則的行，以 `DiagnosticSeverity.Error` （紅色波浪線）取代 `DiagnosticSeverity.Warning` （綠色波浪線）。 規則的其餘部分會從您在逐步解說開頭附近編輯的資源中初始化。 您也需要報告波浪線的位置，這是物件建立運算式的型別規格的位置。 在 [`if`] 區塊中輸入下列程式碼：

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

您的函式看起來應該像這樣（可能會有不同的格式）：

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

請移除中斷點，讓您可以看到您的分析器運作（並停止返回 Visual Studio 的第一個實例）。 將執行指標拖曳至方法的開頭，然後按**F5**繼續執行。 當您切換回 Visual Studio 的第二個實例時，編譯器會開始再次檢查程式碼，而它會呼叫您的分析器。 您可以在 [`ImmutableType<int>`] 底下看到波浪線。

## <a name="adding-a-code-fix-for-the-code-issue"></a>加入程式碼問題的「程式碼修正」

開始之前，請先關閉 Visual Studio 的第二個實例，然後在 Visual Studio 的第一個實例（您正在開發分析器的位置）停止偵錯工具。

**加入新的類別。** 在**方案總管**的專案節點上，使用快捷方式功能表（右指標按鈕），然後加入宣告新的專案。 新增名為 `BuildCodeFixProvider`的類別。 這個類別必須衍生自 `CodeFixProvider`，而且您必須使用**Ctrl**+ **。** （period）以叫用加入正確 `using` 語句的程式碼修正。 這個類別也必須以 `ExportCodeFixProvider` 屬性來標注，而且您必須加入 `using` 語句來解析 `LanguageNames` 列舉。 您應該會有一個類別檔案，其中包含下列程式碼：

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**存根 out 衍生的成員。** 現在，將編輯器的插入號放在識別碼 `CodeFixProvider`，然後按下**Ctrl**+ **。** （期間），以將此抽象基類的實作為存根。 這會為您產生屬性和方法。

**執行屬性。** 使用下列程式碼填入 `FixableDiagnosticIds` 屬性的 `get` 主體：

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn 藉由比對這些識別碼（只是字串）來整合診斷和修正。 專案範本會為您產生診斷識別碼，您可以隨意變更它。 屬性中的程式碼只會從分析器類別傳回識別碼。

**RegisterCodeFixAsync 方法會採用內容。** 內容很重要，因為程式碼修正可以套用至多個診斷，或一行程式碼可能會有一個以上的問題。 如果您輸入 "coNtext" （內容）。 在方法的主體中，IntelliSense 完成清單會顯示一些有用的成員。 有一個 CancellationToken 成員可供您查看是否有任何專案想要取消修正。 有很多有用成員的檔成員，可讓您取得專案和方案模型物件。 其中有一個 Span 成員，這是您在報告診斷時所指定之程式碼位置的開始和結束。

**將方法設為非同步。** 您需要做的第一件事，就是將產生的方法宣告修正為 `async` 方法。 設定抽象類別的程式碼修正不會包含 `async` 關鍵字，即使方法傳回 `Task`也一樣。

**取得語法樹狀結構的根目錄。** 若要修改程式碼，您必須產生新的語法樹狀結構，其中包含您的程式碼修正所進行的變更。 您需要內容中的 `Document`，才能呼叫 `GetSyntaxRootAsync`。 這是非同步方法，因為取得語法樹狀結構的工作不明，可能包括從磁片取得檔案、剖析該檔案，以及為其建立 Roslyn 程式碼模型。 在這段期間，Visual Studio UI 應該會回應，這會使用 `async` 啟用。 將方法中的程式程式碼取代為下列內容：

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**找出有問題的節點。** 您會傳入內容的範圍，但您找到的節點可能不是您必須變更的程式碼。 所報告的診斷只提供類型識別碼的範圍（波浪線所屬），但您需要取代整個物件建立運算式，包括開頭的 `new` 關鍵字和結尾的括弧。 將下列程式碼新增至您的方法（並使用**Ctrl**+ **。** 若要加入 `ObjectCreationExpressionSyntax`的 `using` 語句）：

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**註冊燈泡 UI 的程式碼修正。** 當您註冊程式碼修正時，Roslyn 會自動插入 Visual Studio 燈泡 UI。 終端使用者會看到他們可以使用**Ctrl**+ **。** （期間）：當您的分析器波浪線不正確的 `ImmutableArray<T>` 的函式時，請使用。 因為您的程式碼修正提供者只會在發生問題時執行，所以您可以假設您有要尋找的物件建立運算式。 從內容參數，您可以將下列程式碼新增至 `RegisterCodeFixAsync` 方法的結尾，以註冊新的程式碼修正：

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

您必須將編輯器的插入號放在識別碼中，`CodeAction`，然後使用**Ctrl**+ **。** （period）為此型別加入適當的 `using` 語句。

然後將編輯器的插入號放在 `ChangeToImmutableArrayEmpty` 識別碼中，並使用**Ctrl**+ **。** 同樣地，為您產生此方法存根。

您新增的最後一個程式碼片段會藉由傳遞 `CodeAction` 和所發現問題種類的診斷識別碼，來註冊程式碼修正。 在此範例中，只有一個診斷識別碼，此程式碼會針對提供修正，因此您可以只傳遞診斷識別碼陣列的第一個元素。 當您建立 `CodeAction`時，您會傳入燈泡 UI 應該用來做為程式碼修正描述的文字。 您也會傳入接受 CancellationToken 的函式，並傳回新的檔。 新檔具有新的語法樹狀結構，其中包含呼叫 `ImmutableArray.Empty`的修補後程式碼。 此程式碼片段會使用 lambda，讓它可以在 objectCreation 節點和內容的檔上關閉。

**建立新的語法樹狀結構。** 在您稍早產生其存根的 `ChangeToImmutableArrayEmpty` 方法中，輸入程式程式碼： `ImmutableArray<int>.Empty;`。 如果您再次看到 [ **Syntax Visualizer**工具] 視窗，您可以看到此語法為 SimpleMemberAccessExpression 節點。 這就是這個方法需要在新檔中進行結構和傳回的功能。

`ChangeToImmutableArrayEmpty` 的第一次變更是在 `Task<Document>` 之前加入 `async`，因為程式碼產生器無法假設方法應該是非同步。

使用下列程式碼填入本文，讓您的方法看起來像下面這樣：

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

您必須將編輯器的插入號放在 `SyntaxGenerator` 識別碼中，然後使用**Ctrl**+ **。** （period）為此型別加入適當的 `using` 語句。

這段程式碼會使用 `SyntaxGenerator`，這是用來建立新程式碼的實用型別。 取得具有程式碼問題之檔的產生器之後，`ChangeToImmutableArrayEmpty` 會呼叫 `MemberAccessExpression`，傳遞具有我們想要存取之成員的類型，並將成員的名稱當做字串傳遞。

接下來，方法會提取檔的根目錄，因為這可能牽涉到一般案例中的任意工作，所以程式碼會等候此呼叫並傳遞解除標記。 Roslyn 程式碼模型是不可變的，像是使用 .NET 字串;當您更新字串時，會取得傳回的新字串物件。 當您呼叫 `ReplaceNode`時，您會收到新的根節點。 大部分的語法樹狀結構都是共用的（因為它是不可變的），但是 `objectCreation` 的節點會取代為 `memberAccess` 節點，以及最多到語法樹狀結構根目錄的所有父節點。

## <a name="try-your-code-fix"></a>試用您的程式碼修正

您現在可以按**F5** ，在 Visual Studio 的第二個實例中執行您的分析器。 開啟您先前使用的主控台專案。 現在您應該會看到燈泡出現 `ImmutableArray<int>`的新物件建立運算式。 如果您按下**Ctrl**+ **。** （期間），接著您會看到您的程式碼修正，而且您會在燈泡 UI 中看到自動產生的程式碼差異預覽。 Roslyn 會為您建立此程式。

**Pro 提示：** 如果您啟動 Visual Studio 的第二個實例，而且沒有看到您的程式碼修正的燈泡，則可能需要清除 Visual Studio 元件快取。 清除快取會強制 Visual Studio 重新檢查元件，因此 Visual Studio 接著會取得最新的元件。 首先，關閉 Visual Studio 的第二個實例。 然後，在**Windows Explorer**中，流覽至 [ *%LOCALAPPDATA%\Microsoft\VisualStudio\16.0Roslyn\\* ]。 （"16.0" 會從版本變更為具有 Visual Studio 的版本）。刪除子目錄*ComponentModelCache*。

## <a name="talk-video-and-finish-code-project"></a>討論影片和完成程式碼專案

您可以在[這](https://channel9.msdn.com/events/Build/2015/3-725)段演講中，看到此範例的開發和討論。 這段演講會示範運作中的分析器，並逐步引導您建立程式。

您可以在[這裡](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)看到所有已完成的程式碼。 子資料夾*DoNotUseImmutableArrayCollectionInitializer*和*DoNotUseImmutableArrayCtor*都有一個C#檔案，用於尋找問題，以及C#一個檔案來執行在 Visual Studio 燈泡 UI 中顯示的程式碼修正。 請注意，完成後的程式碼會有更多的抽象概念，以避免 > 類型物件的\<ImmutableArray 上一次提取。 它會使用已嵌套的已註冊動作，將類型物件儲存在可在每次執行子動作（分析物件建立和分析集合初始化）時使用的內容中。

## <a name="see-also"></a>請參閱

* [\\\Build 2015 談](https://channel9.msdn.com/events/Build/2015/3-725)
* [GitHub 上的完整程式碼](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [GitHub 上的數個範例，分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS 網站上的其他檔](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [在 GitHub 上使用 Roslyn 分析器所執行的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
