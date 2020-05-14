---
title: 用於不可改變陣列的羅斯林分析儀和代碼感知庫 |微軟文件
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65849a3d9ad1cdd073551f96e61997fe5f91118a
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444891"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>適用於 ImmutableArray 的 Roslyn 分析器和程式碼感知程式庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[.NET 編譯器平臺](https://github.com/dotnet/roslyn)("Roslyn") 可説明您構建代碼感知庫。 代碼感知庫提供了可以使用和工具(Roslyn 分析器)的功能,以説明您以最佳方式使用庫或避免錯誤。 本主題介紹如何在使用[NIB:不可改變的集合](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca)NuGet 包時構建真實世界 Roslyn 分析器來捕獲常見錯誤。 該示例還演示如何為分析器找到的代碼問題提供代碼修復。 使用者在 Visual Studio 燈泡 UI 中看到代碼修復,並可以自動應用代碼的修復程式。

## <a name="getting-started"></a>開始使用
編譯此範例需要以下內容:

- Visual Studio 2015(不是速成版)或更高版本。 您可以使用免費[的視覺工作室社區版](https://www.visualstudio.com/products/visual-studio-community-vs)

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 您還可以在安裝 Visual Studio 時,在「通用工具」下檢查可視化工作室擴展工具以同時安裝 SDK。 如果您已經安裝了 Visual Studio,還可以通過造訪主功能表**檔&#124;"新&#124;專案"來**安裝此 SDK,在左側導航窗格中選擇 C#,然後選擇"可擴充性」。。 當您選擇「**安裝可視化工作室擴展工具**」麵包屑專案範本時,它會提示您下載並安裝 SDK。

- [.NET 編譯器平臺 ("羅斯林") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). 您還可以透過存取主選單**檔案&#124;"新&#124;專案'** 來安裝此 SDK,在左側導航窗格中選擇**C#,** 然後選擇 **「可擴充性**」。 當您選擇「**下載.NET 編譯器平臺 SDK」** 麵包屑專案樣本時,它會提示您下載並安裝 SDK。 此 SDK 包含[為 Kkk 的 Kkk 的工具 。](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer) 這個非常有用的工具可説明您找出應在分析器中尋找的程式碼模型類型。 分析器基礎結構會調用代碼以進行特定的代碼模型類型,因此代碼僅在必要時執行,並且只能專注於分析相關代碼。

## <a name="whats-the-problem"></a>怎麼了?
假設您提供了一個包含不可改變陣列(例如)<xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>支援的庫。 C# 開發人員在 .NET 陣列方面擁有豐富的經驗。 但是,由於實現中使用的 ImmutableArray 和優化技術的性質,C# 開發人員直覺會導致庫的使用者編寫損壞的代碼,如下所述。 此外,使用者在運行時之前不會看到自己的錯誤,這不是他們在帶有 .NET 的 Visual Studio 中習慣的質量體驗。

使用者熟悉編寫代碼,如下所示:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

創建空數組以填充後續代碼行並使用集合初始化器語法是 C# 開發人員非常熟悉的。 但是,為執行時的不可改變陣列崩潰編寫相同的代碼:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

第一個錯誤是由於 ImmutableArray 實現使用結構來包裝基礎數據存儲。 結構必須具有無參數建構函數,`default(T)`以便表示式可以返回包含所有零或空成員的結構。 當代碼存`b1.Length`取 時,存在運行時 null 取消引用錯誤,因為 ImmutableArray 結構中沒有基礎儲存陣列。 建立空白無法改變陣列的正確方法是`ImmutableArray<int>.Empty`。

 集合初始化程序出現錯誤的原因是 ImmutableArray.Add 方法每次調用時都會返回新實例。 由於 ImmutableArray 永遠不會更改,因此在添加新元素時,您將獲得一個新的 ImmutableArray 物件(出於性能原因,該物件可能與以前存在的 ImmutableArray 共用儲存)。 因為`b2`在呼`Add()`叫五次之前指向第一個不可改變陣列`b2`, 因此是預設的不可改變陣列。 調用長度上也崩潰與空取消引用錯誤。 在不手動呼叫 Add 的正確方法是使用`ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`。

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>尋找觸發分析器的相關語法節點類型
要開始構建分析器,首先確定需要查找的語法Node類型。   從選單**檢視&#124;其他 Windows &#124;罗斯林语法可视化工具启动语法可视化器**。

將編輯器的圖子放在宣告 的行`b1`上 。 您將看到語法可視化器顯示您位於語法樹的`LocalDeclarationStatement`節點中。 此節點有`VariableDeclaration`一個 ,它反`VariableDeclarator`過來 又有`EqualsValueClause`一個 ,`ObjectCreationExpression`最後有一個 。 當您按一下節點的語法可視化器樹時,編輯器視窗中的語法將突出顯示以顯示該節點表示的代碼。 語法節點子類型的名稱與 C# 語法中使用的名稱匹配。

## <a name="creating-the-analyzer-project"></a>建立分析器項目
從主選單中選擇**檔案&#124;新&#124;專案...** 在"**新項目**"對話框中,在左側導航欄中的**C#** 專案下,選擇「可擴充性」,並在右側窗格中選擇 **「具有代碼修復器」專案範本的「分析器**」 "。 輸入名稱並確認對話方塊。

樣本將打開DiagnosticAnalyzer.cs檔。 選擇該編輯器緩衝區選項卡。此檔具有從`DiagnosticAnalyzer`(Roslyn API 類型)派生的分析器類(由您給專案的名稱構成)。 您的新類具有聲明`DiagnosticAnalyzerAttribute`分析器與 C# 語言相關的聲明,以便編譯器發現並載入分析器。

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

您可以使用適用於 C# 程式碼的 Visual Basic 實現分析器,反之亦然。 在診斷分析器屬性中,選擇分析器是針對一種語言還是兩種語言更為重要。 需要詳細建模語言的更複雜的分析器只能針對一種語言。 例如,如果分析器僅檢查類型名稱或公共成員名稱,則可以使用 Roslyn 跨 Visual Basic 和 C# 提供的通用語言模型。 例如,FxCop 警告類<xref:System.Runtime.Serialization.ISerializable>實現 ,但類沒有獨立<xref:System.SerializableAttribute>於語言的屬性,適用於 Visual Basic 和 C# 代碼。

## <a name="initalizing-the-analyzer"></a>使分析儀的去功能化
在類別中`DiagnosticAnalyzer`移至捲動一點來`Initialize`檢視方法 。 啟動分析器時編譯器呼叫此方法。 該方法採用一個`AnalysisContext`物件,該物件允許分析器獲取上下文資訊,併為要分析的代碼類型註冊事件回調。

```csharp
public override void Initialize(AnalysisContext context) {}
```

在此方法中打開一條新行,併鍵入"上下文"。 查看"感知完成清單"。 您可以在完成清單中看到有許多`Register…`方法可以處理各種事件。 例如,第一個,`RegisterCodeBlockAction`調用回您的代碼塊,這通常是代碼之間的大括弧。 註冊塊還會調用到代碼,用於欄位的初始化器、給定到屬性的值或可選參數的值。

另一個示例`RegisterCompilationStartAction`在編譯開始時調用回代碼,當您需要收集多個位置的狀態時,這非常有用。 您可以建立資料結構,例如,收集使用的所有符號,每次調用分析器以查找某些語法或符號時,都可以保存有關資料結構中每個位置的資訊。 當您由於編譯結束而被回調時,可以分析保存的所有位置,例如,報告代碼使用每個`using`語句的符號。

使用**語法可視化工具**,您瞭解到當編譯器處理 Object 創造運算式時,您希望被調用。 使用此代碼設定回檔:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

註冊語法節點,並僅註冊對象創建語法節點的篩選器。 按照慣例,分析器作者在註冊操作時使用 lambda,這有助於使分析器保持無狀態。 您可以使用「**從使用方式產生**」視覺工作室功能`AnalyzeObjectCreation`來創建 該方法。 這也會為您生成正確的上下文參數類型。

## <a name="setting-properties-for-users-of-your-analyzer"></a>為分析器使用者設定屬性
因此,您的分析器適當地顯示在 Visual Studio UI 中,請查找並修改以下代碼行以識別分析器:

```csharp
internal const string Category = "Naming";
```

將 `"Naming"` 變更為 `"API Guidance"`。

使用**解決方案資源管理員**在專案中尋找並打開資源.resx 檔案。 您可以為分析器、標題等提供說明。您可以將所有這些`“Don’t use ImmutableArray<T> constructor”`值更改為現在。 您可以將字串格式參數放在字串中 (、{0}{1}等),稍後調用`Diagnostic.Create()`時 ,可以提供要傳遞的參數參數參數的參數陣列。

## <a name="analyzing-an-object-creation-expression"></a>剖析物件建立式式
該方法`AnalyzeObjectCreation`採用代碼分析器框架提供的不同類型的上下文。 初始化方法`AnalysisContext`允許您註冊操作回調以設置分析器。 例如`SyntaxNodeAnalysisContext`,有一`CancellationToken`個可以傳遞的。 如果用戶開始鍵入編輯器,Roslyn 將取消運行分析器以節省工作並提高性能。 另一個範例是,此上下文具有返回物件創建語法節點的 Node 屬性。

取得節點,您可以假定該節點是篩選語法節點操作的類型:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>首次使用分析器啟動視覺化工作室
通過構建和執行分析器啟動可視化工作室(按**F5)。** 由於**解決方案資源管理器**中的啟動專案是 VSIX 專案,因此執行代碼將生成代碼和 VSIX,然後啟動安裝了該 VSIX 的可視化工作室。 以這種方式啟動 Visual Studio 時,它會使用不同的註冊表配置單元啟動,這樣您在構建分析器時對 Visual Studio 的主要使用不會受到測試實例的影響。 首次以這種方式啟動時,Visual Studio 會執行多個初始化,類似於安裝後首次啟動 Visual Studio 時的初始化。

 建立主控台項目,然後將陣列碼輸入到主控台應用程式中 Main 方法:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

帶`ImmutableArray`的代碼行有波浪形,因為您需要獲取不可變的 NuGet 包`using`並將語句 添加到代碼中。 按**解決方案資源管理器**中專案節點上的右指標按鈕,然後選擇 **「管理 NuGet 包..."。** 在 NuGet 管理器中,在搜尋框中鍵入"不可改變" ,並在左側窗格中選擇"System.集合.不可改變"(不要選擇"Microsoft.Bcl.Immu 可量")項,然後按右側窗格中的「安裝」按鈕。 安裝包會添加對專案引用的引用。

您仍然看到紅色波浪下`ImmutableArray`,所以將插入器放在該標識符中,然後按**CTRL+。** (期間)以顯示建議的修復功能表並選擇添加適當的`using`語句。

**立即保存所有實例並關閉**Visual Studio 的第二個實例,以將您置於乾淨狀態以繼續。

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>使用編輯並繼續完成分析器
在 Visual Studio 的第一個實例中,通過在第`AnalyzeObjectCreation`一行上 按**F9**與加斯特一起在方法的開頭設置斷點。

使用**F5**再次啟動分析器,在 Visual Studio 的第二個實例中,重新打開上次創建的控制台應用程式。

返回到斷點處 Visual Studio 的第一個實例,因為 Roslyn 編譯器看到對象創建表達式並調用到分析器中。

**獲取對象創建節點。** 以按**F10**`objectCreation`和**在「立即視窗**」`“objectCreation.ToString()”`中計算表達式,單步執行設置變數的行。 您可以看到,變數指向的語法節點是代碼`"new ImmutableArray<int>()"`,這正是您要查找的代碼。

**獲取不可改變的陣列\<T>类型对象。** 您需要檢查正在建立的類型是否為不可改變陣列。 首先,獲取表示此類型的物件。 使用語義模型檢查類型,以確保您擁有完全正確的類型,並且不會比較 ToString() 中的字串。 在函數末尾輸入以下代碼行:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

在中使用回引號 (') 和泛型參數數指定泛型類型。 這就是為什麼你沒有看到"...元數據名稱中的不可\<可變數組 T>"。

語義模型有許多有用的東西,允許您詢問有關符號、數據流、變數存留期等的問題。由於各種工程原因(性能、建模錯誤代碼等),Roslyn 將語法節點與語義模型分開。 您希望編譯模型查找引用中包含的資訊,以便進行準確的比較。

您可以在編輯器視窗的左側拖動黃色執行指標。 將其拖動到設置變數的`objectCreation`行,並使用**F10**跨過新代碼行。 如果將滑鼠指標懸停在變數`immutableArrayOfType`上,則發現我們在語義模型中找到了確切的類型。

**獲取對象創建表達式的類型。** 本文以多種方式使用"Type",但這意味著如果您有"新 Foo"運算式,則需要獲取 Foo 的模型。 您需要取得物件建立表示式的類型,以查看它是不可改變的 Array\<T> 類型。 再次使用語義模型獲取對象創建表達式中類型符號(不可改變陣列)的符號資訊。 在函數末尾輸入以下代碼行:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

由於分析器需要處理編輯器緩衝區中不完整或不正確的程式碼(例如,缺少語`using`句),因此應檢查`symbolInfo`是否`null`為 。 您需要從符號資訊物件中獲取命名類型(I命名類型符號)才能完成分析。

**比較類型。** 由於我們要查找的 T 的開放式泛型類型,並且代碼中的類型是具體的泛型類型,因此您查詢符號資訊,瞭解類型來自什麼(開放泛型類型),並將該`immutableArrayOfTType`結果與 進行比較。 在方法的末尾輸入以下內容:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**報告診斷。** 報告診斷非常簡單。 在初始化方法之前定義的專案樣本中,可以使用為您創建的規則。 由於代碼中的此情況是錯誤的,因此您可以將初始化規則替換`DiagnosticSeverity.Warning`的行(綠色波浪)替換`DiagnosticSeverity.Error`為 (紅色波浪)。 規則的其餘部分從演練開頭附近編輯的資源初始化。 您還需要報告波浪的位置,即對象創建表達的類型規範的位置。 輸入此代碼`if`:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

您的函數應如下所示(可能採用不同的格式):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}

```

刪除斷點,以便可以看到分析器工作(並停止返回到 Visual Studio 的第一個實例)。 將執行指標拖動到方法的開頭,然後按**F5**繼續執行。 當您切換回 Visual Studio 的第二個實例時,編譯器將開始再次檢查代碼,並將調用到分析器中。 您可以在`ImmutableType<int>`下 看到一個波浪形。

## <a name="adding-a-code-fix-for-the-code-issue"></a>為代碼問題添加"代碼修復"
開始之前,關閉 Visual Studio 的第二個實例,並在 Visual Studio 的第一個實例(您正在開發分析器)中停止調試。

**添加新類。** 在解決方案資源管理器中的專案節點上使用快捷方式功能表(右指標按鈕),然後選擇添加新項。 添加名為`BuildCodeFixProvider`的類。 此類需要派生自`CodeFixProvider`,並且您需要使用**CTRL+。** (期間)以調用添加正確`using`語句的代碼修復程式。 此類還需要使用`ExportCodeFixProvider`屬性進行說明,並且需要添加語`using`句`LanguageNames`來解決 枚舉。 應該有一個包含以下代碼的類別檔:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**存出派生成員。** 現在,將編輯器的插入符放在標識符`CodeFixProvider`中,然後按**CTRL+。** (期間)以存根此抽象基類的實現。 這將為您產生屬性和方法。

**實現屬性。** 使用以下代碼`FixableDiagnosticIds`填寫`get`屬性 的正文:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn 透過對這些識別碼(只是字串)來組合診斷和修復。 項目範本為您生成了診斷 ID,您可以自由更改它。 屬性中的代碼只是從分析器類返回 ID。

**註冊代碼修復同步方法採用上下文。** 上下文很重要,因為代碼修復可以應用於多個診斷,或者代碼行上可能有多個問題。 如果鍵入"上下文"。 在該方法的正文中,Intellisense 完成清單將顯示一些有用的成員。 有一個取消令牌成員,您可以檢查,看看是否有東西要取消修復。 有一個 Document 成員,它有許多有用的成員,允許您訪問專案和解決方案模型物件。 有一個 Span 成員是報告診斷時指定的代碼位置的開始和結束。

**使該方法是異步的。** 您需要做的第一`async`件事是將生成的方法聲明固定為方法。 將抽象類別的程式庫取得的程式碼修復不包括關鍵字`async`, 即使方法`Task`傳回 。

**獲取語法樹的根。** 要修改代碼,您需要使用代碼修復程式所做的更改生成新的語法樹。 您必須`Document`從上下文中呼叫`GetSyntaxRootAsync`。 這是一個非同步方法,因為有未知的工作來獲取語法樹,可能包括從磁碟獲取檔,對其進行解析,並為它構建 Roslyn 程式碼模型。 Visual Studio UI 應在此期間`async`回應,使用 啟用。 將方法中的代碼行取代為以下內容:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**查找問題節點。** 在上下文的範圍內傳遞,但找到的節點可能不是必須更改的代碼。 報告的診斷僅提供類型識別碼(波浪形屬於的位置)的跨度,但您需要替換整個物件創建表達式,包括開頭的`new`keywoard 和末尾的括弧。 將以下代碼添加到方法(並使用**CTRL+)。** 為添加`using``ObjectCreationExpressionSyntax`語句。

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **註冊燈泡 UI 的代碼修復程式。** 註冊代碼修復程式時,Roslyn 會自動插入 Visual Studio 燈泡 UI。 最終使用者將看到他們可以使用**CTRL+。** (句點)當分析器切換不良`ImmutableArray<T>`構造函數使用時。 由於代碼修復提供程式僅在出現問題時執行,因此可以假定您具有要查找的物件創建表達式。 從上下文參數中,您可以通過將以下代碼添加到方法末`RegisterCodeFixAsync`尾 來註冊新的代碼修復:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

您需要將編輯器的插入符放在識別子中,`CodeAction`然後使用**CTRL+。** (期間)以添加此類型的`using`相應語句。

然後,將編輯器的插入符放在標識符中`ChangeToImmutableArrayEmpty`並使用**CTRL+。** 再次為您生成此方法存根。

您添加的最後一個程式碼段通過傳遞 找到的問題`CodeAction`類型的 和診斷 ID 來註冊代碼修復。 在此示例中,此代碼僅提供一個診斷 ID,因此只需傳遞診斷 ID 陣列的第一個元素即可。 建立時,`CodeAction`將 傳遞燈泡 UI 應用程式程式修復說明的文字。 您還可以傳遞一個函數,該函數採用取消令牌並返回新文檔。 新文檔有一個新的語法樹,其中包含調`ImmutableArray.Empty`用的修補代碼。 此程式碼段使用 lambda,以便它可以關閉物件創建節點和上下文的文檔。

**構造新的語法樹。** 在前面產生`ChangeToImmutableArrayEmpty`存根的方法中,輸入代碼行: `ImmutableArray<int>.Empty;`。 如果再次查看語法可視化工具工具視窗,則可以看到此語法是簡單成員訪問表達式節點。 這是此方法需要在新的文檔中建構和返回的內容。

第一個更改`ChangeToImmutableArrayEmpty`是`Task<Document>`之前`async`添加 ,因為代碼產生器不能假定該方法應該是非同步的。

使用以下代碼填充正文,以便方法看起來類似於以下內容:

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

您需要將編輯器的插入符放在識別子中`SyntaxGenerator`並使用**CTRL+。** (期間)以添加此類型的`using`相應語句。

此代碼使用`SyntaxGenerator`,這是構建新代碼非常有用的類型。 取得具有代碼問題的文件的生成器後,`ChangeToImmutableArrayEmpty`呼`MemberAccessExpression`叫、傳遞具有要存取的成員的類型,並將成員的名稱作為字串傳遞。

接下來,該方法獲取文檔的根,由於這可能涉及一般情況下的任意工作,因此代碼等待此調用並傳遞取消權杖。 Roslyn 程式碼模型是不可變的,就像使用 .NET 字串一樣;更新字串時,您將獲得一個新的字串物件作為回報。 當您呼叫`ReplaceNode`時,您會傳回一個新的根節點。 大多數語法樹是共用的(因為它是不可變的),但`objectCreation`節點被`memberAccess`節點以及語法樹根的所有父節點替換。

## <a name="trying-your-code-fix"></a>嘗試代碼修復
現在,您可以按**F5**在 Visual Studio 的第二個實例中執行分析器。 打開以前使用的主控台專案。 現在,您應該看到燈泡出現在新對象創建表達式的`ImmutableArray<int>`所在 位置。 如果按**CTRL+。** (期間),然後您將看到代碼修復程式,並在燈泡 UI 中看到自動生成的代碼差異預覽。 羅斯林為你創造這個

專業提示:如果您啟動 Visual Studio 的第二個實例,而您看不到帶有代碼修復功能的燈泡,則可能需要清除 Visual Studio 元件緩存。 清除緩存將強制 Visual Studio 重新檢查元件,因此 Visual Studio 應選取最新的元件。 首先,關閉視覺工作室的第二個實例。 在 Windows 資源管理員中,轉到使用者目錄 (c:\\\使用者\><使用rid), 並找到 AppData_本地\Microsoft_VisualStudio_14.0Roslyn\\。 在此目錄中,刪除子目錄元件模型快取。 "14"將版本更改為具有 Visual Studio 的版本。

## <a name="talk-video-and-finish-code-project"></a>討論視訊和完成代碼項目
你可以看到這個例子在[本文](https://channel9.msdn.com/events/Build/2015/3-725)中得到進一步開發和討論。 談話演示了工作分析器,並引導您完成構建它。

你可以[在這裡](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)看到所有完成的代碼。 子資料夾"不用Immu可尋形收集初始化器"和"不用不可改變的ArrayCtor"各有一個用於查找問題的 C# 檔和一個 C# 檔,用於實現顯示在 Visual Studio 燈泡 UI 中的代碼修復。 請注意,已完成的代碼具有多一點的抽象,以避免一遍又一遍地獲取 ImmutableArray\<T>类型对象。 它使用嵌套註冊的操作將類型物件保存在執行子操作(分析物件創建和分析集合初始化)時可用的上下文中。

## <a name="see-also"></a>另請參閱
[\\*構建 2015 年討論](https://channel9.msdn.com/events/Build/2015/3-725)
 
[GitHub 上已完成的代碼](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)[GitHub 上的幾個範例,分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md) 
[其他文檔,在 GitHub OSS 網站](https://github.com/dotnet/roslyn/tree/master/docs/analyzers) 
[FxCop 規則上使用 GitHub 上的 Roslyn 分析器實現](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
