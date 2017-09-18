---
title: "Roslyn 分析器和 ImmutableArrays 感知程式碼程式庫 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Roslyn 分析器和 ImmutableArrays 感知程式碼程式庫
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[.NET 編譯器平台](https://github.com/dotnet/roslyn) \("Roslyn"\) 可協助您建置感知程式碼程式庫。  感知程式碼程式庫提供您可以使用的功能和工具 \(Roslyn 分析器\) 可協助您使用程式庫的最佳方式，或為了避免發生錯誤。  本主題說明如何建置真實世界的 Roslyn 分析器來使用時，攔截常見錯誤 [不可變的集合](../Topic/NIB:%20Immutable%20Collections.md) NuGet 封裝。  此範例也示範如何提供分析器\] 中所找到的程式碼問題的程式碼修正。  使用者會看到 Visual Studio 燈泡 UI 中的程式碼修正程式，並自動套用的修正程式碼。  
  
## 本主題內容  
 本主題包括下列各節 ︰  
  
-   使用者入門  
  
-   什麼是問題?  
  
-   尋找相關的程式碼模型的型別來觸發程式分析器  
  
-   建立分析專案  
  
-   初始化分析器  
  
-   設定您的分析師的使用者屬性  
  
-   分析的物件建立運算式  
  
-   使用您的分析程式第一次啟動 Visual Studio  
  
-   完成分析師使用編輯後繼續  
  
-   加入 「 程式碼修復 」 的程式碼問題  
  
-   嘗試您的程式碼修正  
  
-   討論視訊中和已完成的程式碼專案  
  
## 使用者入門  
 您需要下列項目建置這個範例:  
  
-   Visual Studio 2015 \(非 Express Edition\) 或更新版本。  您可以使用免費 [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  您也可以 Visual Studio 中，在安裝時檢查下一次安裝 SDK 的一般工具的 Visual Studio 擴充性工具。  如果您已安裝 Visual Studio，您也可以安裝此 SDK，請前往 \[主要功能表 **檔案 &#124;新 &#124;專案...**, ，在左的導覽窗格中選擇 C\#，然後選擇 \[擴充性。  當您選擇 「**安裝 Visual Studio 擴充性工具**"階層連結專案範本，它會提示您下載並安裝 SDK。  
  
-   [.NET 編譯器平台 \("Roslyn"\) SDK](http://aka.ms/roslynsdktemplates)。  您也可以安裝此 SDK，請前往 \[主要功能表 **檔案 &#124;新 &#124;專案...**, 、 選擇 **C\#** 左瀏覽窗格中，然後選擇 **擴充性**。  當您選擇 「**下載.NET 編譯器平台 SDK**"階層連結專案範本，它會提示您下載並安裝 SDK。  此 SDK 包含 [Roslyn 語法視覺化檢視](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)。  這非常有用的工具可協助您找出哪些程式碼模型類型您應該在尋找您的分析師。  分析器基礎結構會呼叫至您的程式碼的特定程式碼模型類型，因此您的程式碼只在必要時執行而且可以專注只分析相關的程式碼。  
  
## 什麼是問題?  
 想像一下您 ImmutableArray 提供的程式庫 \(例如， <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>\) 支援。  C\# 開發人員有許多接觸.NET 陣列。  不過，由於 ImmutableArrays 和最佳化技術，用於實作中，C\# 開發人員 intuitions 會造成使用者的程式庫撰寫中斷的程式碼，如下所述。  此外，使用者不會看到其錯誤到執行階段，這並不是在 Visual Studio.net 中用來體驗品質。  
  
 使用者熟悉撰寫程式碼如下所示:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 建立空的陣列，以填入後續幾行程式碼，並使用集合初始設定式語法是 C\# 開發人員非常熟悉。  不過，撰寫相同程式碼 ImmutableArray 損毀在執行階段:  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 第一個錯誤是因為 ImmutableArray 實作使用包裝的基礎資料存放區結構。  結構必須具有無參數建構函式，讓 `default(T)` 運算式可能會傳回所有結構零或 null 的成員。  當程式碼存取 `b1.Length`, ，沒有執行的階段 null 取值錯誤，因為 ImmutableArray 結構中沒有任何基礎的存放裝置陣列。  若要建立空的 ImmutableArray 的正確方式是 `ImmutableArray<int>.Empty`。  
  
 集合初始設定式的錯誤是因為 ImmutableArray.Add 方法就會傳回新的執行個體，每次呼叫它。  由於 ImmutableArrays 永遠不會變更，當您新增新的項目時，您將收到新的 ImmutableArray 物件 \(這可能與先前已存在的 ImmutableArray 共用儲存體，基於效能考量\)。  因為 `b2` 指向第一個呼叫之前，先 ImmutableArray `Add()` 五次， `b2` 是 ImmutableArray 預設值。  長度上呼叫它也為 null 的當機取值錯誤。  初始化 ImmutableArray，而不以手動方式呼叫 Add 来使用的正確方式 `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`。  
  
## 尋找相關的語法來觸發程式分析器的節點型別  
 若要開始建置分析器\] 中，先找出您要尋找 SyntaxNode 的類型。    啟動語法視覺化檢視，從功能表 **檢視 &#124;其他視窗 &#124;Roslyn 語法視覺化檢視**。  
  
 將編輯器的插入號放在宣告行 `b1`。  您會看到語法視覺化檢視會顯示您在 `LocalDeclarationStatement` 語法樹狀結構的節點。  這個節點有 `VariableDeclaration`, ，因而具有 `VariableDeclarator`, ，因而具有 `EqualsValueClause`, ，最後還有 `ObjectCreationExpression`。  當您按一下在語法視覺化檢視樹狀目錄中的節點，\[編輯器\] 視窗中的語法反白顯示，以顯示該節點所代表的程式碼。  SyntaxNode 子類型的名稱符合 C\# 文法中使用的名稱。  
  
## 建立分析專案  
 從主要功能表選擇 \[ **檔案 &#124;新 &#124;專案...**。  在 **新的專案** 對話方塊下方 **C\#** 專案在左側的導覽列中，選擇擴充性\]，在右窗格中選擇 **與修正程式碼分析器** 專案範本。  輸入的名稱，並確認對話方塊。  
  
 範本開啟 DiagnosticAnalyzer.cs 檔案。  選擇該編輯器緩衝區\] 索引標籤。  此檔案具有分析器類別 \(形成您為資料庫專案的名稱\)，衍生自 `DiagnosticAnalyzer` \(Roslyn API 型別\)。  新的類別具有 `DiagnosticAnalyzerAttribute` 宣告您的分析師是 C\# 語言相關，如此，編譯器會探索並載入您的分析師。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 您可以實作使用以 C\# 程式碼，為目標的 Visual Basic 分析器，反之亦然。  請務必更 DiagnosticAnalyzerAttribute，選擇您的分析目標一種語言，或兩者中。  更複雜的分析器需要詳細模型化的語言可以只針對單一語言。  如果您分析器\] 中，例如，只會檢查型別名稱或公用成員名稱，可能可以使用 Visual Basic 和 C\# 的 Roslyn 提供通用的語言模型。  比方說，FxCop 會警告類別會實作 <xref:System.Runtime.Serialization.ISerializable>, ，但是類別並沒有 <xref:System.SerializableAttribute> 屬性與語言無關，而且適用於 Visual Basic 和 C\# 程式碼。  
  
## 初始化分析器  
 中向下捲動有點 `DiagnosticAnalyzer` 類別，以查看 `Initialize` 方法。  啟用分析程式 」 時，編譯器會呼叫這個方法。  此方法會採用 `AnalysisContext` 物件，可讓您分析程式以取得內容資訊，以及如何註冊您想要分析的程式碼類型的事件的回呼。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 開啟新的一行中這個方法和型別 「 內容 」。 若要查看的 Intellisense 完成清單。  您所見，完成清單中有許多 `Register…` 來處理各種事件的方法。  例如，在第一個 `RegisterCodeBlockAction`, ，通常是大括號之間的程式碼區塊的程式碼呼叫。  註冊區塊也會回呼您的程式碼初始設定式的欄位、 屬性，指定的值或選擇性參數的值。  
  
 例如， `RegisterCompilationStartAction`, ，呼叫您的程式碼在編譯時，您需要收集許多位置狀態的開頭。  您可以建立資料結構，例如收集所有的符號，以及每次您分析師會回呼部分語法或符號，可以儲存每個位置的相關資訊，在您的資料結構。  當您正在編譯結束由於回撥時，可以分析您儲存，例如，報告程式碼會從每個使用何種符號的所有位置 `using` 陳述式。  
  
 使用 **語法視覺化檢視**, ，您已了解您要編譯器處理 ObjectCreationExpression 時呼叫。  您可以使用此程式碼來設定回呼:  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 您註冊語法節點，然後只物件建立語法節點的篩選條件。  依照慣例，分析器作者 lambda 註冊時，使用有助於保護分析器無狀態的動作。  您可以使用 Visual Studio 功能 **從使用量產生** 建立 `AnalyzeObjectCreation` 方法。  這會產生正確的內容參數類型為您太。  
  
## 設定您的分析師的使用者屬性  
 使您的分析師會出現在 Visual Studio UI 適當，尋找並修改下列一行程式碼，以識別您的分析師:  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 變更 `"Naming"` 到 `"API Guidance"`。  
  
 接下來尋找並開啟 Resources.resx 檔案在專案中使用 **方案總管\] 中**。  您可以將描述在您的分析師、 標題等。您可以變更所有的這些值 `“Don’t use ImmutableArray<T> constructor”` 現在。  您可以將格式字串中的引數的字串 \({0} {\\{1\\} 等\)，及更新版本，當您呼叫 `Diagnostic.Create()`, ，您可以提供要傳遞引數的 params 陣列。  
  
## 分析的物件建立運算式  
 `AnalyzeObjectCreation` 方法會採用不同類型的程式碼分析器架構所提供的內容。  Initialize 方法 `AnalysisContext` 可讓您註冊動作來設定您的分析師的回呼。`SyntaxNodeAnalysisContext`, ，比方說，具有 `CancellationToken` 周圍，您可以傳遞。  如果使用者啟動編輯器中輸入，Roslyn 將會取消執行分析器，以儲存工作並改善效能。  另一個範例，此內容可傳回的物件建立語法節點的節點屬性。  
  
 取得節點中，您可以假設您已篩選的語法節點動作的類型:  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
### 使用您的分析程式第一次啟動 Visual Studio  
 藉由建置並執行您的分析師啟動 Visual Studio \(按 **F5**\)。  因為啟動專案的 **方案總管\] 中** 是 VSIX 專案，您的程式碼和 VSIX，執行您的程式碼的組建，然後啟動 \[Visual Studio 安裝的 VSIX。  當您啟動 Visual Studio，如此一來時，它會啟動相異的登錄 hive，因此主要使用的 Visual Studio 將不會受到您測試的執行個體建立分析器時。  第一次啟動如此一來，Visual Studio 會執行數個類似於當您第一次啟動 Visual Studio 安裝完成後的初始設定。  
  
 建立主控台專案，然後輸入您主控台應用程式的 Main 方法中的陣列程式碼:  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 程式碼行 `ImmutableArray` 有波浪線，因為您需要取得不可變的 NuGet 封裝，並新增 `using` 陳述式，以您的程式碼。  中的專案節點上按右指標按鈕 **方案總管\] 中** 選擇 **Manage NuGet Packages...**。  在 NuGet 管理員，在 \[搜尋\] 方塊中，輸入 「 不可變 」 然後選擇 \[項目 「 System.Collections.Immutable 」 \(未選擇 「 Microsoft.Bcl.Immutable 」\) 中的左的窗格和按下 \[安裝\] 按鈕，在右窗格中。  安裝套件加入至您的專案參考的參考。  
  
 您仍然會看到紅色的波浪線下方 `ImmutableArray`, ，因此將插入號放在該識別項和按 **CTRL \+。** \(句號\) 可顯示建議的修正程式功能表，然後選擇 \[新增適當 `using` 陳述式。  
  
 **全部儲存並關閉** 能讓您在乾淨狀態繼續目前的 Visual Studio 的第二個執行個體。  
  
## 完成分析師使用編輯後繼續  
 在 Visual Studio 的第一個執行個體，設定中斷點的開頭您 `AnalyzeObjectCreation` 方法藉由按下 **F9** 與第一行上插入號。  
  
 啟動一次使用您分析器 **F5**, ，然後在 Visual Studio 的第二個執行個體，重新開啟您最後一次建立主控台應用程式。  
  
 您會回到 Visual Studio 的第一個執行在中斷點，因為 Roslyn 編譯器所看到的物件建立運算式和名為您的分析師。  
  
 **取得物件建立節點。**步驟設定的線路 `objectCreation` 變數按 **F10**, ，然後在 **即時運算視窗** 評估運算式 `“objectCreation.ToString()”`。  您可以看到變數會指向語法節點是程式碼 `"new ImmutableArray<int>()"`, ，只您所尋找的內容。  
  
 **取得 ImmutableArray \< T \> 類型的物件。**您需要檢查 ImmutableArray 是否正在建立的類型。  首先，您會取得表示這個類型的物件。  您會檢查以確保一個正確的類型，而且您不比較 tostring \(\) 的字串中使用語意模型的類型。  輸入下列行結尾的函式的程式碼:  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 您指定泛型型別與 backquotes \('\) 的中繼資料和泛型參數的數目。  這就是為什麼看不到"...ImmutableArray \< T \>"中的中繼資料名稱。  
  
 語意模型上，可讓您發問符號、 資料流程、 變數存留期等等，有許多有用的事情。Roslyn 語意模型中來分隔語法節點，基於各種工程 \(效能、 模型等錯誤的程式碼。\)。  您想要查閱的精確比較參考資料中包含的資訊編譯模型。  
  
 您可以拖曳黃色執行指標編輯器視窗的左邊。  將它拖曳至 \[設定列 `objectCreation` 變數和不進入您的程式碼使用新的一行 **F10**。  如果您將滑鼠指標停留在變數 `immutableArrayOfType`, ，您會看到我們語意模型中找到正確的類型。  
  
 **取得物件建立運算式的型別。**「 類型 」 會使用幾種方法，在本文中，但這表示如果您有 「 新的 Foo"運算式中，您需要取得 Foo 的模型。  您需要取得物件建立運算式，以查看它是否 ImmutableArray \< T \> 類型的類型。  取得物件建立運算式中的型別符號 \(ImmutableArray\) 的符號資訊一次使用語意模型。  輸入下列行結尾的函式的程式碼:  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 因為您分析器會需要處理不完整或不正確的程式碼編輯器緩衝區中 \(例如，沒有遺漏 `using` 陳述式\)，您應該檢查 `symbolInfo` 正在 `null`。  您需要取得具名型別 \(INamedTypeSymbol\) 中的符號資訊物件，才能完成分析。  
  
 **比較型別。**有，我們要的 T 為開放式泛型類型，並且在程式碼中的型別是具體的泛型型別，因為查詢從 \(開放式的泛型型別\) 建構的何種類型的符號資訊和比較的結果與 `immutableArrayOfTType`。  輸入在方法結尾處:  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 **報告診斷。**報告診斷是這麼簡單。  您使用專案範本，其定義之前的 Initialize 方法中為您建立的規則。  因為這種情況下，在程式碼錯誤，您可以變更初始化規則來取代一行 `DiagnosticSeverity.Warning` \(綠色波浪線\) 與 `DiagnosticSeverity.Error` \(紅色波浪線\)。  此規則的其餘部分初始化您附近的逐步解說開始編輯的資源。  您也需要報表的位置在波浪線，這是物件建立 expresssion 類型規格的位置。  輸入此代碼 `if` 區塊:  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 您的函式看起來應該像這樣 \(或許是格式不同\):  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 移除中斷點，讓您可以看到分析器工作 \(並停止回到 Visual Studio 的第一個執行個體\)。  執行指標拖曳至您的方法，並按下開頭 **F5** 繼續執行。  當您切換回 Visual Studio 的第二個執行個體時，編譯器便會開始再次強調，檢查程式碼，它會呼叫至您的分析師。  您可以看到在曲線 `ImmutableType<int>`。  
  
## 加入 「 程式碼修復 」 的程式碼問題  
 在開始之前，關閉 Visual Studio 的第二個執行個體，並停止偵錯 \(其中您正在開發 「 分析器 」\) 的 Visual Studio 的第一個執行個體中。  
  
 **加入新的類別。**您在 \[方案總管\] 中的專案節點上使用的捷徑功能表 \(右指標按鈕\)，然後選擇 \[新增新的項目。  加入類別，稱為 `BuildCodeFixProvider`。  這個類別必須衍生自 `CodeFixProvider`, ，而且您必須使用 **CTRL \+。** \(句號\) 來叫用加入正確的程式碼修正 `using` 陳述式。  這個類別也必須以註解 `ExportCodeFixProvider` 屬性，而且您必須將 `using` 陳述式，以解決 `LanguageNames` 列舉。  您應該在它為下列程式碼的類別檔案:  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 **清除衍生的成員。**現在，將編輯器\] 的插入號放在識別項 `CodeFixProvider` 按 **CTRL \+。** \(句號\) 以移除這個抽象基底類別的實作。  這會為您產生的屬性和方法。  
  
 **實作的屬性。**填寫 `FixableDiagnosticIds` 屬性的 `get` 本文中的下列程式碼:  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
 Roslyn 結合診斷和修正藉由比對這些識別項都是字串。  專案範本產生診斷的識別碼，並沒有變更。  屬性中的程式碼只會傳回從分析器類別識別碼。  
  
 **RegisterCodeFixAsync 方法會採用內容。**內容非常重要的因為程式碼修正可以套用到多個診斷，或在程式碼的行上可能有一個以上的問題。  如果您輸入 「 內容 」。 在方法主體中，Intellisense 完成清單將示範一些實用的成員。  沒有 CancellationToken 成員，您可以檢查看看項目是否要取消此修正程式。  沒有文件成員具有許多實用的成員，並可讓您取得的專案和方案的模型物件。  Span 的成員開頭和結尾的程式碼位置指定當您報告診斷。  
  
 **請為非同步方法。**首先您需要執行的是修正產生的方法宣告為 `async` 方法。  抽象類別的實作依虛設常式的程式碼修正不包含 `async` 關鍵字即使方法會傳回 `Task`。  
  
 **取得語法樹狀目錄的根目錄。**若要修改的程式碼會產生新的語法樹狀結構的變更可讓您的程式碼修正。  您需要 `Document` 從呼叫內容 `GetSyntaxRootAsync`。  因為未知的工作，以取得語法樹狀目錄中，可能會包含從磁碟中取得檔案、 剖析，並建置 Roslyn 程式碼模型，這是非同步方法。  在此期間，使用 Visual Studio UI 應該有回應 `async` 啟用。  在方法中的程式碼行取代為下列:  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
 **找到與問題的節點。**您傳入的內容範圍內，但您會發現可能不是您必須變更的程式碼的節點。  報告的診斷只提供範圍 \(其中在波浪線所屬\) 的型別識別項，但您需要取代整個物件建立運算式，包括 `new` keywoard 開頭和結尾括號。  將下列程式碼加入至您的方法 \(使用 **CTRL \+。** 新增 `using` 陳述式 `ObjectCreationExpressionSyntax`\):  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
 **註冊您的程式碼修正的燈泡 UI。**當您註冊您的程式碼修正時，Roslyn 外掛到 Visual Studio 燈泡 UI 自動。  使用者將會看到他們可以使用 **CTRL \+。** \(句號\) 當您分析的波浪線錯誤 `ImmutableArray<T>` 建構函式使用。  因為您的程式碼修正提供者只會執行的問題時，您可以假設您有您要尋找的物件建立運算式。  從內容參數，您可以註冊新的程式碼修正的結尾加入下列程式碼 `RegisterCodeFixAsync` 方法:  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
 您必須將編輯器的插入號放在識別項， `CodeAction`, ，然後使用 **CTRL \+。** \(句號\) 加入適當 `using` 這種類型的陳述式。  
  
 然後將放置在編輯器的插入號 `ChangeToImmutableArrayEmpty` 識別項和使用 **CTRL \+。** ，為您產生方法 stub。  
  
 您加入這個最後一個程式碼片段將註冊的程式碼修正 `CodeAction` 和診斷的識別碼，找到問題的種類。  在此範例中，有一個只診斷的識別碼，此程式碼提供修正程式，讓您可以只將診斷識別碼陣列的第一個項目。  當您建立 `CodeAction`, ，即會傳入燈泡 UI 應該使用程式碼修正程式的描述文字。  您也會傳遞的函式會採用 CancellationToken 並傳回新的文件中。  新的文件中有新的語法樹狀結構，其中包含您的修補程式碼會呼叫 `ImmutableArray.Empty`。  此程式碼片段會使用 lambda，讓它可以透過 objectCreation 節點和內容的文件關閉。  
  
 **建構新的語法樹狀結構。**在 `ChangeToImmutableArrayEmpty` 您稍早產生的虛設常式輸入一行程式碼的方法: `ImmutableArray<int>.Empty;`。  如果您再次檢視語法視覺化檢視工具視窗，您可以看到這個語法是 SimpleMemberAccessExpression 節點。  這是這個方法需要建構，並傳回新的文件中。  
  
 第一個變更 `ChangeToImmutableArrayEmpty` 是加入 `async` 之前 `Task<Document>` 因為程式碼產生器不能假設方法應該是非同步。  
  
 使您的方法看起來類似下面的填入內容取代為下列程式碼:  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
 您必須將編輯器\] 的插入號放在 `SyntaxGenerator` 識別項和使用 **CTRL \+。** \(句號\) 加入適當 `using` 這種類型的陳述式。  
  
 此程式碼使用 `SyntaxGenerator`, ，這是一種非常好用來建構新的程式碼。  取得文件產生器的程式碼問題之後, `ChangeToImmutableArrayEmpty` 呼叫 `MemberAccessExpression`, 、 傳遞具有我們想要存取的成員的類型和成員的名稱傳遞為字串。  
  
 接著，方法會擷取的文件根，因為這可能包含任意的工作，在一般情況下，程式碼等候此呼叫，並傳遞的取消語彙基元。  Roslyn 的程式碼模型是固定不變，類似於處理.NET 字串;當您更新字串時，會傳回取得新的字串物件。  當您呼叫 `ReplaceNode`, ，您將收到新的根節點。  大部分的語法樹狀目錄的共用 \(因為它是不可變的\)，但 `objectCreation` 節點取代 `memberAccess` 節點，以及直到語法樹狀目錄根的父節點。  
  
## 嘗試您的程式碼修正  
 您現在可以按 **F5** Visual Studio 的第二個執行個體中執行您的分析師。  開啟您以前使用的主控台專案。  現在您應該會看到燈泡出現新的物件建立運算式的 `ImmutableArray<int>`。  如果您按下 **CTRL \+。** \(時間\)，然後您會看到您的程式碼修正，且您將看到燈泡 UI 中的自動產生的程式碼差異預覽。  Roslyn 為您建立這。  
  
 Pro 提示: 如果您啟動 Visual Studio 中，第二個執行個體，而且您沒有看到燈泡與您的程式碼修正，則您可能需要清除的 Visual Studio 元件快取。  清除快取會強制 Visual Studio 來重新檢查元件，讓 Visual Studio 應會挑選您最新的元件。  首先，關閉 Visual Studio 的第二個執行個體。  然後在 Windows 檔案總管，請移至您的 user 目錄 \(c:\\users\\ \< 識別碼 \>\)，找出 AppData\\Local\\Microsoft\\VisualStudio\\14.0Roslyn\\。  在此目錄中，刪除子目錄 ComponentModelCache。  版本與 Visual Studio"14"變更。  
  
## 討論影片和完成的程式碼專案  
 您可以看到此範例中所開發，並討論中進一步 [這段演講](http://channel9.msdn.com/events/Build/2015/3-725)。  演講將示範使用分析程式，並引導您完成建置它。  
  
 您可以看到所有完成的程式碼 [這裡](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)。  DoNotUseImmutableArrayCollectionInitializer 和 DoNotUseImmutableArrayCtor 每個子資料夾有 C\# 檔案中找出問題並實作顯示在 Visual Studio 燈泡 UI 的程式碼修正程式的 C\# 檔案。  請注意，完成的程式碼有一些多個抽象概念，以避免重複擷取 ImmutableArray \< T \> 型別物件。  它所提供的內容中儲存的型別物件會使用巢狀的已註冊的動作時子動作 \(分析物件的建立和分析集合初始設定\) 執行。  
  
## 請參閱  
 [\\\\Build 2015年通話](http://channel9.msdn.com/events/Build/2015/3-725)   
 [在 github 上的完整程式碼](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)   
 [在 github 上的數個範例分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)   
 [OS github 網站上的其他文件](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)   
 [使用 Roslyn 分析器 github 上實作的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)