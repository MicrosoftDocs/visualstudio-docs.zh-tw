---
title: Microsoft Help Viewer SDK |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 96647f362566f0687cb04b7da4459331ac56b031
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851910"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本文包含 Visual Studio 說明檢視器整合者的下列工作：

- 建立主題（F1 支援）

- 建立 Help Viewer 內容-商標套件

- 部署一組文章

- 將說明新增至 Visual Studio shell （整合模式或獨立模式）

- 其他資源

### <a name="creating-a-topic-f1-support"></a>建立主題（F1 支援）
 本節概述呈現主題的元件、主題需求、如何建立主題的簡短描述（包括 F1 支援需求），最後是範例主題及其轉譯結果。

 **說明檢視器主題總覽**

 當針對轉譯呼叫主題時，說明檢視器會在安裝或上次更新時取得與主題相關聯的商標套件專案，以及主題 XHTML，並結合這兩個專案以產生顯示的內容視圖（商標資料 +主題資料）。  商標套件包含標誌、內容行為的支援，以及商標文字（著作權等等）。  如需商標套件元素的詳細資訊，請參閱下方的「建立品牌封裝」。  如果沒有與主題相關聯的商標套件，說明檢視器將會使用位於說明檢視器應用程式根目錄中的「回溯品牌」套件（Branding_en-US. .mshc）。

 **說明檢視器主題需求**

 若要在說明檢視器中正確轉譯，原始主題內容必須是 W3C Basic 1.1 XHTML。

 主題通常包含兩個區段：

- 中繼資料（請參閱內容中繼資料參考）：主題的相關資料，例如主題唯一識別碼、關鍵字值、主題 TOC ID、父節點識別碼等等。

- 本文內容：與 W3C Basic 1.1 XHTML 相容，其中包括支援的內容行為（可折迭的區域、程式碼片段等。完整清單如下所示。

  Visual Studio 商標套件支援的控制項：

- 「連結」

- CodeSnippet

- CollapsibleArea

- 繼承的成員

- LanguageSpecificText

  支援的語言字串（不區分大小寫）：

- javascript

- csharp 或 c#

- cplusplus 或 visualc + + 或 c + +

- jscript

- ... 或 vb

- f # 或 fsharp.core 或 fs

- other –代表語言名稱的字串

  **建立 Help Viewer 主題**

  建立名為 ContosoTopic4 的新 XHTML 檔案，並包含 title 標記（下方）。

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

 接下來，新增資料以定義要如何呈現主題（自我標識）、如何參考本主題中的 F1、此主題是否存在於目錄中、其識別碼（適用于其他主題的連結參考）等等。 如需所支援中繼資料的完整清單，請參閱下面的「內容中繼資料」表格。

- 在此情況下，我們將使用自己的商標套件，這是一種 Visual Studio 說明檢視器商標套件的變體。

- 新增 F1 元名稱和值（"Microsoft. Help. F1" content = "ContosoTopic4"），其會符合 IDE 屬性包中提供的 F1 值。  （如需詳細資訊，請參閱 F1 支援一節）。  這是在 IDE 中選擇 F1 時，與 IDE 內的 F1 呼叫相符合的值。

- 新增主題 ID。 這是其他主題用來連結到本主題的字串。  這是本主題的說明檢視器識別碼。

- 針對 TOC，新增這個主題的父節點，以定義此主題 TOC 節點的顯示位置。

- 針對 TOC，新增本主題的節點順序。 當父節點具有 n 個子節點數目時，請依照子節點的位置來定義。 例如，本主題是4個子主題的第4節）。

  範例中繼資料區段：

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>

```

 **主題主體**

 主題的主體（不包括頁首和頁尾）將包含頁面連結、附注區段、可折迭區域、程式碼片段，以及語言特定文字的區段。  請參閱商標一節，以取得有關所呈現主題區域的資訊。

1. 新增主題標題標記： `<div class="title">Contoso Topic 4</div>`

2. 新增附注區段： `<div class="alert"> add your table tag and text </div>`

3. 新增可折迭的區域： `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. 新增程式碼片段： `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. 新增程式碼語言特定文字： `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` 請注意，devLangnu = 可讓您輸入其他語言。 例如，devLangnu = "Fortran" 會在程式碼片段 DisplayLanguage = Fortran 時顯示 Fortran

6. 新增頁面連結： `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> 注意：在程式碼片段中不支援的新 [顯示語言] F#（例如，、Cobol、Fortran）程式碼顏色標示會是單色。

 **範例說明檢視器主題**此程式碼說明如何定義中繼資料、程式碼片段、可折迭區域和語言特定文字。

```
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>

```

 **F1 支援**

 在 Visual Studio 中，選取 F1 會產生從 IDE 內的游標位置所提供的值，並以提供的值填入「屬性包」（根據游標位置而定）。 當資料指標超過功能 x 時，功能 x 會處於作用中/已聚焦，並以值填入屬性包。  當選取 F1 時，會填入屬性包，並 Visual Studio F1 程式碼查看客戶預設的說明來源為本機或線上（線上為預設值），然後根據使用者設定建立適當的字串（online 為預設值）-shell 執行（如需本機說明為預設值，請參閱說明系統管理員指南中的 exe 啟動參數），以及參數清單中有關鍵詞的 MSDN URL （若有的話）。

 如果為 F1 傳回三個字串，稱為多重值字串，請採用第一個詞彙，尋找點擊次數，如果找到，我們就完成了;如果不是，請移至下一個字串。  順序很重要。 多值關鍵字的呈現方式應為最短字串的最長字串。  若要在多重值關鍵字的情況下進行驗證，請查看線上 F1 URL 字串，其中將包含所選的關鍵字。

 在 Visual Studio 2012 中，我們刻意在線上和離線之間進行更強的劃分，因此，如果使用者的設定是在線上，則我們只會直接將 F1 要求傳遞至 MSDN 上的線上查詢服務，而不是透過 Help Library 代理程式路由傳送我們在 Visual Studio 2010 中。 然後，我們會依賴「安裝的廠商內容 = true」的狀態，來判斷是否要在內容中執行不同的動作。 若為 true，則會根據您想要為客戶支援的內容，執行此剖析和路由邏輯。 若為 false，則只會前往 MSDN。 如果使用者的設定為 [本機]，則所有呼叫都會移至本機說明引擎。

 F1 流程圖：

 ![F1 流程](../../extensibility/internals/media/f1flow.png "F1flow")

 當說明檢視器預設說明內容來源設定為線上時（在瀏覽器中啟動）：

- Visual Studio Partner （VSP）功能會對 F1 屬性包（屬性包前置詞）發出值。在登錄中找到的前置詞的關鍵字和線上 URL）： F1 會將 VSP URL + 參數傳送至瀏覽器。

- Visual Studio 功能（語言編輯器、Visual Studio 特定功能表項目等）： F1 將 Visual Studio URL 傳送至瀏覽器。

  當說明檢視器預設說明內容來源設定為 [本機說明] 時（在說明檢視器中啟動）：

- .VSP 功能，其中 F1 屬性包與本機存放區索引（也就是屬性包前置詞. 關鍵字 = 在本機存放區索引中找到的值）之間的關鍵字比對： F1 會在說明檢視器中呈現主題。

- Visual Studio 功能（不會有 VSP 用來覆寫從 Visual Studio 功能發出的屬性包）： F1 會在說明檢視器中呈現 Visual Studio 主題。

  設定下列登錄值，以啟用 [廠商說明] 內容的 F1 回溯。 F1 回溯表示說明檢視器設定為在線上尋找 F1 說明內容，而廠商內容是安裝在本機的使用者硬碟上。 [說明檢視器] 應該會查看內容的本機說明，雖然預設設定是用於線上說明。

1. 在 Help 2.1 登錄機碼底下設定**VendorContent**值：

   - 32位作業系統：

        HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = dword：00000001

   - 64位作業系統：

        HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = dword：00000001

2. 在 Help 2.1 登錄機碼下註冊夥伴命名空間：

   - 32位作業系統：

      HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Help\v2.1\Partner<em>\\< 命名空間\></em>

      「位置」 = 「離線」

   - 64位作業系統：

      HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Partner<em>\\< 命名空間\></em>

      「位置」 = 「離線」

   **基底原生命名空間剖析**

   若要開啟基底原生命名空間剖析，請在登錄中新增 DWORD，其名稱為： BaseNativeNamespaces，並將其值設定為1（在所要支援的類別目錄索引鍵底下）。  例如，如果您想要使用 Visual Studio 目錄，您可以將金鑰新增至路徑：

   HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   遇到格式標頭/方法中的 F1 關鍵字時，將會剖析 '/' 字元，產生下列結構：

- 標頭：將會是可以用來在登錄中註冊的命名空間

- 方法：這會成為通過的關鍵字。

  例如，假設有一個稱為 CustomLibrary 的自訂程式庫，以及一個名為 MyTestMethod 的方法，當 F1 要求傳入時，會將其格式化為 `CustomLibrary/MyTestMethod`。

  然後，使用者可以將 CustomLibrary 註冊為合作夥伴 hive 底下的命名空間，並提供所需的任何位置索引鍵，並將 MyTestMethod 傳遞至查詢的關鍵字。

  **在 IDE 中啟用協助調試工具**

  新增下列登錄機碼和值：

  HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\12.0\Dynamic 說明索引鍵：顯示零售價值中的調試輸出值：是

  在 IDE 的 [說明] 功能表項目底下，選取 [Debug Help CoNtext]

  **內容中繼資料**

  在下表中，方括弧之間出現的任何字串都是必須由可辨識的值取代的預留位置。 例如，在 \<meta name = "Microsoft. Help. Locale" content = "[語言代碼]"/>，"[language code]" 必須以 "en-us" 之類的值取代。

|屬性（HTML 表示）|描述|
|--------------------------------------|-----------------|
|\< meta name = "Microsoft. Help. Locale" content = "[language-code]"/>|設定本主題的地區設定。 如果主題中使用此標籤，則必須只使用該標籤一次，而且必須在任何其他 Microsoft Help 標記的上方插入。 如果未使用此標記，則會使用與產品地區設定相關聯的斷詞工具（如果有指定的話）來編制主題的主體文字的索引。否則，會使用 en-us 斷詞工具。 此標記符合 ISOC RFC 4646。 若要確保 Microsoft 說明能正常運作，請使用這個屬性，而不是一般語言屬性。|
|\< meta name = "TopicLocale" content = "[language-code]"/>|當其他地區設定也在使用時，為本主題設定地區設定。 如果主題中使用此標記，則必須只使用一次。 當目錄包含多個語言的內容時，請使用此標記。 目錄中的多個主題可以有相同的識別碼，但每個都必須指定唯一的 TopicLocale。 指定符合目錄地區設定之 TopicLocale 的主題，是顯示在目錄中的主題。 不過，所有語言版本的主題都會顯示在搜尋結果中。|
|\< 標題 > [標題]\</title >|指定本主題的標題。 此標記為必要項，而且在主題中必須只使用一次。 如果主題主體未包含標題 \<div > 區段，則此標題會顯示在主題和目錄中。|
|\< meta name = "Microsoft. Help. 關鍵字" content = "[aKeywordPhrase]"/>|指定在 [說明檢視器] 的 [索引] 窗格中顯示之連結的文字。 按一下連結時，就會顯示主題。您可以為主題指定多個索引關鍵字，或者，如果您不想要此主題的連結出現在索引中，可以省略這個標記。 舊版說明的 "K" 關鍵字可以轉換成這個屬性。|
|\< meta name = "Microsoft. Help. Id" content = "[TopicID]"/>|設定本主題的識別碼。 此標記為必要項，而且在主題中必須只使用一次。 識別碼在具有相同地區設定的目錄中的主題中必須是唯一的。 在另一個主題中，您可以使用此識別碼來建立此主題的連結。|
|\< meta name = "Microsoft. Help. F1" content = "[IRecyclingItemContainerGenerator]"/>|指定此主題的 F1 關鍵字。 您可以為主題指定多個 F1 關鍵字，或者，如果您不想要在應用程式使用者按下 F1 時顯示這個主題，可以省略這個標記。 一般來說，主題只會指定一個 F1 關鍵字。 舊版說明中的 "F" 關鍵字可以轉換成這個屬性。|
|\< 中繼名稱 = "Description" content = "[主題描述]"/>|提供本主題中內容的簡短摘要。 如果主題中使用此標記，則必須只使用一次。 此屬性是由查詢程式庫直接存取;它不會儲存在索引檔案中。|
 meta name = "TocParent" content = "[parent_Id]"/>|在目錄中指定本主題的父主題。 此標記為必要項，而且在主題中必須只使用一次。 值是父項的 Microsoft.Help.Id。 一個主題在目錄中可以只有一個位置。 "-1" 視為目錄根的主題識別碼。 在 [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]中，該頁面是 Help Viewer 首頁。 這就是我們特別將 TocParent =-1 新增至某些主題，以確保它們顯示在最上層的原因。[說明檢視器] 首頁是系統頁面，因此不可取代。 如果 VSP 嘗試新增識別碼為-1 的頁面，它可能會加入至內容集，但說明檢視器一律會使用系統頁面–說明檢視器首頁|
|\< meta name = "TocOrder" content = "[正整數]"/>|指定本主題在目錄中顯示的位置，相對於其對等主題。 此標記為必要項，而且在主題中必須只使用一次。 值為整數。 指定較低值之整數的主題會出現在指定較高值整數的主題上方。|
|\< 中繼名稱 = "Microsoft. Help. 產品" content = "[產品代碼]"/>|指定本主題所描述的產品。 如果主題中使用此標記，則必須只使用一次。 這種資訊也可以當做傳遞至說明索引子的參數來提供。|
|\< meta name = "ProductVersion" content = "[版本號碼]"/>|指定本主題所描述的產品版本。 如果主題中使用此標記，則必須只使用一次。 這種資訊也可以當做傳遞至說明索引子的參數來提供。|
|\< 中繼名稱 = "Microsoft. Help. Category" content = "[string]"/>|供產品用來識別內容的小節。 您可以識別主題的多個子區段，如果您不想要連結來識別任何子區段，也可以省略此標記。 當主題從舊版的說明轉換時，此標記用來儲存 TargetOS 和 TargetFrameworkMoniker 的屬性。 內容的格式為 AttributeName： AttributeValue。|
|\< meta name = "TopicVersion content =" [主題版本號碼] "/>|當目錄中有多個版本時，指定此版本的主題。 由於 Microsoft.Help.Id 不保證是唯一的，因此當目錄中有多個版本的主題時，就需要此標記，例如，當目錄包含 .NET Framework 3.5 的主題時，以及 .NET Framework 4 的主題，而且兩者都有相同的微軟.Help.Id。|
|\< meta name = "SelfBranded" content = "[TRUE 或 FALSE]"/>|指定本主題是否使用 Help Library 管理員啟動商標套件，或主題專屬的商標套件。 這個標記必須是 TRUE 或 FALSE。 若為 TRUE，則相關主題的品牌封裝會覆寫 Help Library 管理員啟動時所設定的商標套件，如此一來，即使該主題與其他內容的轉譯不同，也會將其轉譯為預期。 如果為 FALSE，則會根據 Help Library 管理員啟動時所設定的商標套件來轉譯目前的主題。 根據預設，除非 SelfBranded 變數宣告為 TRUE，否則 Help Library 管理員會將自我商標視為 false。因此，您不需要宣告 \<meta name = "SelfBranded" content = "FALSE"/>。|

### <a name="creating-a-branding-package"></a>建立商標套件
 Visual Studio 版本包含許多不同的 Visual Studio 產品，包括 Visual Studio 合作夥伴的隔離和整合式 shell。  這些產品都需要某種程度的以主題為基礎的說明內容商標支援，這對產品而言是唯一的。  例如，Visual Studio 的主題必須有一致的品牌展示，而將 ISO Shell 包裝在一起的 SQL Studio 則需要自己獨特的每個主題的說明內容商標。  整合式 Shell 合作夥伴可能會希望其說明主題位於父系 Visual Studio 產品說明內容中，同時維護自己的主題品牌。

 品牌套件是由包含說明檢視器的產品所安裝。  針對 Visual Studio 產品：

- 「說明檢視器」語言套件中會安裝一個「回溯品牌」套件（Branding_\<locale >. .mshc）至說明檢視器2.1 應用程式根目錄（範例： C:\Program Files （x86） \Microsoft Help Viewer\v2.1）。  這適用于未安裝產品商標套件的情況（未安裝任何內容）或安裝的品牌封裝已損毀的情況。  使用應用程式根回退商標套件時，會忽略 Visual Studio 元素（標誌和意見反應）。

- 從內容套件服務安裝 Visual Studio 內容時，也會一併安裝商標套件（適用于第一次內容安裝案例）。  如果已更新商標套件，則會在下一次內容更新或其他套件安裝動作發生時安裝更新。

  Microsoft Help Viewer 支援以主題中繼資料為基礎的主題商標。

- 其中主題中繼資料會定義自我標記 = true，依情況轉譯主題，不執行任何動作（最遠為商標）。

- 當主題元資料定義自我標記 = false 時，請使用與 TopicVendor 中繼資料值相關聯的商標套件。

- 其中主題元資料定義 name = "TopicVendor" content = 廠商 .MSHA > 中\< 商標套件名稱，請使用在內容值中定義的商標套件。

- 在 Visual Studio 目錄中，有一個優先的品牌封裝應用程式。  Visual Studio 首先會套用預設的商標，然後，如果在主題中繼資料中定義，並支援相關聯的品牌封裝（如安裝 .msha 中所定義），則會將廠商定義的商標套用為覆寫。

  商標元素通常分為三個主要類別：

- Header 元素（範例包括意見反應連結、條件免責聲明文字、標誌）

- 內容行為（範例包括展開/折迭控制項文字元素和程式碼片段元素）

- 頁尾元素（範例著作權）

  視為品牌要素的專案包括（此規格中詳述）：

- 目錄/產品標誌（例如，Visual Studio）

- 意見反應連結和電子郵件元素

- 免責聲明文字

- 著作權文字

  Visual Studio 說明檢視器商標套件中支援的檔案包括：

- 圖形（標誌、圖示等）

- 商標 .js –支援內容行為的腳本檔案

- 商標 .xml –跨目錄內容一致使用的字串。  注意：如需 Visual Studio 商標 .xml 中的當地語系化文字元素，請包含 _locID = "\<唯一值 >"

- 商標 .css-呈現一致性的樣式定義

- 列印 .css –一致列印呈現的樣式定義

  如先前所述，品牌套件與主題相關聯：

- 在中繼資料中定義 SelfBranded = false 時，主題會繼承類別目錄商標套件

- 或者，當 SelfBranded = false 時，.MSHA 中定義了唯一的商標套件，而且在安裝內容時可供使用

  對於執行自訂商標套件（VSP content，SelfBranded = True）的 Vsp，其中一種方法是從回溯品牌套件（隨說明檢視器安裝）開始，並視需要變更檔案的名稱。  Branding_\<地區設定 > .mshc 檔案是副檔名已變更為. .mshc 的 zip 檔案，因此只要將副檔名從 .mshc 變更為 .zip 並將內容解壓縮。  請參閱下方的品牌套件元素，並視需要進行修改（例如，將標誌變更為 VSP 標誌，並參考商標 .xml 檔案中的標誌，並更新每一 VSP 規格的商標 .xml 等等）。

  完成所有修改後，請建立包含所需商標元素的 zip 檔案，並將副檔名變更為. .mshc。

  若要建立自訂商標套件的關聯，請建立 .MSHA，其中包含商標 .mshc 檔案的參考以及內容 .mshc （包含主題）。  如需如何建立基本 .MSHA 的詳細說明，請參閱下面的「.MSHA」。

  當主題包含 \<meta name = "SelfBranded" content = "false"/> 時，商標 .xml 檔案包含一份清單元素，用於一致地呈現主題中的特定專案。  以下列出商標 .xml 檔案中的 Visual Studio 元素清單。  這份清單的目的是用來做為 ISO Shell 採用者的範本，在其中修改這些元素（例如標誌、意見反應和著作權）以符合自己的產品品牌需求。

  注意： "{n}" 所注明的變數具有程式碼相依性–移除或變更這些值會導致錯誤，並可能造成應用程式損毀。當地語系化識別碼（例如 _locID = "codesnippet"）包含在 Visual Studio 商標套件中。

  **商標 .xml**

|||
|-|-|
|功能：|**CollapsibleArea**|
|請使用：|展開折迭內容控制項文字|
|**目**|**值**|
|ExpandText|Expand|
|CollapseText|摺疊|
|功能：|**CodeSnippet**|
|請使用：|程式碼片段控制項文字。  注意：具有「非中斷」空間的程式碼片段內容將會變更為「空間」。|
|**目**|**值**|
|CopyToClipboard|複製至剪貼簿|
|ViewColorizedText|檢視|
|CombinedVBTabDisplayLanguage|Visual Basic (範例)|
|VBDeclaration|宣告|
|VBUsage|使用|
|功能：|**意見反應、頁尾和標誌**|
|請使用：|提供意見反應控制項給客戶，以透過電子郵件提供有關目前主題的意見反應。  內容的著作權文字。  標誌定義。|
|**目**|**值（這些字串可以修改以符合內容採用者的需求）。**|
|詳情|© 2013 Microsoft Corporation. All rights reserved.|
|SendFeedback|\<href = "{0}" {1}> 將此主題的意見反應傳送給 Microsoft\<。|
|No-results-found-feedbacklink||
|LogoTitle|[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]|
|LogoFileName|vs_logo_bk .gif|
|LogoFileNameHC|vs_logo_wh .gif|
|功能：|**免責聲明**|
|請使用：|機器轉譯內容的一組案例特定免責聲明。|
|**目**|**值**|
|MT_Editable|本文為機器翻譯。 如果您有網際網路連線，請選取 [線上流覽這個主題]，以同時使用原始英文內容的可編輯模式來觀看此頁面。|
|MT_NonEditable|本文為機器翻譯。 如果您有網際網路連線，請選取 [線上流覽這個主題]，以同時使用原始英文內容的可編輯模式來觀看此頁面。|
|MT_QualityEditable|這篇文章是以手動方式轉譯。 如果您有網際網路連線，請選取 [線上流覽這個主題]，以同時使用原始英文內容的可編輯模式來觀看此頁面。|
|MT_QualityNonEditable|這篇文章是以手動方式轉譯。 如果您有網際網路連線，請選取 [線上流覽這個主題]，以同時使用原始英文內容的可編輯模式來觀看此頁面。|
|MT_BetaContents|本文是針對初稿發行的機器翻譯。 如果您有網際網路連線，請選取 [線上流覽這個主題]，以同時使用原始英文內容的可編輯模式來觀看此頁面。|
|MT_BetaRecycledContents|這篇文章是針對初稿發行而手動翻譯的。 如果您有網際網路連線，請選取 [線上流覽這個主題]，以同時使用原始英文內容的可編輯模式來觀看此頁面。|
|功能：|**LinkTable**|
|請使用：|線上主題連結的支援|
|**目**|**值**|
|LinkTableTitle|連結資料表|
|TopicEnuLinkText|請參閱本主題\</a > 的英文版，這可在您的電腦上取得。|
|TopicOnlineLinkText|觀看本主題 \<href = "{0}" {1}> online\</a >|
|OnlineText|Online|
|功能：|**Video 音訊控制項**|
|請使用：|顯示影片內容的元素和文字|
|**目**|**值**|
|MultiMediaNotSupported|必須安裝 Internet Explorer 9 或更新版本，才能支援 {0} 內容。|
|VideoText|顯示影片|
|AudioText|串流音訊|
|OnlineVideoLinkText|\<p > 若要觀看與本主題相關的影片，請按一下 [{0}\<href = "{1}" >{2}這裡\</a >]。\</p >|
|OnlineAudioLinkText|\<p > 若要接聽與本主題相關的音訊，請按一下 [{0}\<href = "{1}" >{2}這裡\</a >]。\</p >|
|功能：|**內容未安裝控制**|
|請使用：|用於轉譯 contentnotinstalled 的文字元素（字串）|
|**目**|**值**|
|ContentNotInstalledTitle|在您的電腦上找不到任何內容。|
|ContentNotInstalledDownloadContentText|\<p > 若要將內容下載到您的電腦，請 \<href = "{0}" {1}> 按一下 管理 索引標籤\</a >。\</p >|
|ContentNotInstalledText|\<p > 未在您的電腦上安裝任何內容。 請參閱系統管理員以取得本機說明內容安裝。\</p >|
|功能：|**找不到主題控制項**|
|請使用：|用於轉譯 topicnotfound 的文字元素（字串）|
|**目**|**值**|
|TopicNotFoundTitle|在您的電腦上找不到要求的主題。|
|TopicNotFoundViewOnlineText|\<p > 在您的電腦上找不到您要求的主題，但是您可以 \<href = "{0}" {1}> 觀看線上\</a > 主題。\</p >|
|TopicNotFoundDownloadContentText|\<p > 請參閱流覽窗格以取得類似主題的連結，或 \<href = "{0}" {1}> 按一下 管理 索引標籤\</a >，將內容下載到您的電腦。\</p >|
|TopicNotFoundText|\<p > 在您的電腦上找不到您要求的主題。\</p >|
|功能：|**主題損毀控制項**|
|請使用：|用於轉譯 topiccorrupted 的文字元素（字串）|
|**目**|**值**|
|TopicCorruptedTitle|無法顯示要求的主題。|
|TopicCorruptedViewOnlineText|\<p > 說明檢視器無法顯示要求的主題。 主題的內容或基礎系統相依性中可能發生錯誤。\</p >|
|功能：|**首頁控制項**|
|請使用：|支援顯示 [說明檢視器] 最上層節點內容的文字。|
|**目**|**值**|
|HomePageTitle|說明檢視器首頁|
|HomePageIntroduction|\<p > 歡迎使用 Microsoft Help Viewer，這是一種基本的資訊來源，適用于使用 Microsoft 工具、產品、技術和服務的每個人。 說明檢視器可讓您存取 how-to 和參考資訊、範例程式碼、技術文章等等。 若要尋找您所需的內容，請流覽目錄、使用全文檢索搜尋，或使用關鍵字索引流覽內容。\</p >|
|HomePageContentInstallText|\<p >\<br/> 使用 \<a href = "{0}" {1}> 管理內容\</a > 索引標籤來執行下列動作：\<ul >\<li > 將內容新增至您的電腦。\</li >\<li > 檢查您本機內容的更新。\</li >\<li > 從您的電腦移除內容。\</li >\</ul >\</p >|
|HomePageInstalledBooks|已安裝的書籍|
|HomePageNoBooksInstalled|在您的電腦上找不到任何內容。|
|HomePageHelpSettings|說明內容設定|
|HomePageHelpSettingsText|\<p > 您目前的設定是本機說明。 [說明檢視器] 會顯示您已在電腦上安裝的內容。\<br/> 若要變更說明內容的來源，請在 [Visual Studio] 功能表列上，選擇 [\<範圍樣式 = "{0}" > 說明]，將 [說明喜好設定]\</span >。\<br/>\</p >|
|1Mb|MB|

 **商標 .js**

 商標 .js 檔案包含 Visual Studio 說明檢視器商標元素所使用的 JavaScript。  以下是商標元素和支援的 JavaScript 函數清單。  這個檔案的所有要當地語系化的字串都會定義在此檔案頂端的 [可當地語系化的字串] 區段中。  已針對商標 .js 檔案中的 loc 字串建立了 ICL 檔案。

||||
|-|-|-|
|**商標功能**|**JavaScript 函式**|**描述**|
|Var 。||定義變數|
|取得使用者程式碼語言|setUserPreferenceLang|將索引編號對應至程式碼語言|
|設定並取得 cookie 值|System.windows.application.getcookie、System.windows.application.setcookie||
|繼承的成員|changeMembersLabel|展開/折迭繼承的成員|
|當 SelfBranded = False 時|onLoad|讀取查詢字串，以檢查它是否為列印要求。  將所有 codesnippets 設定為將焦點放在 [使用者慣用] 索引標籤。 如果是列印要求，則將 isPrinterFriendly 設定為 true。 檢查高對比模式。|
|程式碼片段|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|將所有可折迭的控制項物件寫入清單中。|
||CA_Click|根據可折迭區域的狀態，定義要呈現的影像和文字|
|標誌的對比支援|isBlackBackground()|呼叫以判斷背景是否為黑色。  只有在高對比模式下才會正確。|
||isHighContrast()|使用彩色範圍來偵測高對比模式|
||onHighContrast （黑色）|偵測到高對比時呼叫|
|.LST 功能|||
||addToLanSpecTextIdSet （id）||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet （lang）||
|多媒體功能|標題（開始、結束、文字、樣式）||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff （id）||
||toSeconds （t）||
||getAllComments （node）||
||styleRectify （styleName，Stylevalue）||
||showCC （id）||
||副標題（id）||

 **HTM 檔案**

 品牌套件包含一組 HTM 檔案，可支援將重要資訊傳達給內容使用者的案例，例如首頁，其中包含描述已安裝內容集的區段，以及當主題無法使用時告訴使用者的頁面。請參閱本地主題集合。 這些 HTM 檔案可以根據每個產品進行修改。  ISO Shell 廠商能夠採用預設商標套件，並變更這些頁面的行為和內容，以符合他們的需求。  這些檔案會參考其各自的商標套件，以便品牌標記從商標 .xml 檔案取得對應的內容。

||||
|-|-|-|
|**檔案**|**用法**|**顯示的內容來源**|
|首頁 .htm|此頁面會顯示目前已安裝的內容，以及任何其他適合使用者呈現其內容的訊息。  此檔案有其他中繼資料屬性 "Microsoft.Help.Id" content = "-1"，這會將此內容放在本機內容目錄的頂端。||
||< META_HOME_PAGE_TITLE_ADD/>|商標 .xml、tag \<HomePageTitle >|
||< HOME_PAGE_INTRODUCTION_SECTION_ADD/>|商標 .xml、tag \<HomePageIntroduction >|
||< HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|商標 .xml、tag \<HomePageContentInstallText >|
||< HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|標題區段商標 .xml 標記\<HomePageInstalledBooks >、從應用程式產生的資料，\<HomePageNoBooksInstalled > 未安裝任何書籍。|
||< HOME_PAGE_SETTINGS_SECTION_ADD/>|標題區段商標 .xml 標記 \<HomePageHelpSettings >，區段文字 \<HomePageHelpSettingsText >。|
|topiccorrupted .htm|當主題存在於本機群組中，但因為某些原因而無法顯示（已損毀的內容）。||
||< META_TOPIC_CORRUPTED_TITLE_ADD/>|商標 .xml、tag \<TopicCorruptedTitle >|
||< TOPIC_CORRUPTED_SECTION_ADD/>|商標 .xml、tag \<TopicCorruptedViewOnlineText >|
|topicnotfound .htm|當本機內容集中找不到主題時，也無法在線上使用||
||< META_TOPIC_NOT_FOUND_TITLE_ADD/>|商標 .xml、tag \<TopicNotFoundTitle >|
||< META_TOPIC_NOT_FOUND_ID_ADD/>|商標 .xml、tag \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||< TOPIC_NOT_FOUND_SECTION_ADD/>|商標 .xml、tag \<TopicNotFoundText >|
|contentnotinstalled .htm|未針對產品安裝任何本機內容時。||
||< META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|商標 .xml、tag \<ContentNotInstalledTitle >|
||< META_CONTENT_NOT_INSTALLED_ID_ADD/>|商標 .xml、tag \<ContentNotInstalledDownloadContentText >|
||< CONTENT_NOT_INSTALLED_SECTION_ADD/>|商標 .xml、tag \<ContentNotInstalledText >|

 **CSS 檔案**

 Visual Studio 說明檢視器品牌套件包含兩個 css 檔案，可支援一致的 Visual Studio 說明內容簡報：

- 商標 .css –包含用於轉譯的 css 元素，其中 SelfBranded = false

- Printer-包含用於轉譯的 css 元素，其中 SelfBranded = false

  商標 .css 檔案包含 Visual Studio 主題呈現的定義（警告是包含在 Branding_\<地區設定中的 .mshc，可能會變更封裝服務的 >。

  **圖形檔案**

  Visual Studio 內容會顯示 Visual Studio 標誌和其他圖形。  Visual Studio 說明檢視器商標套件中的圖形檔完整清單如下所示。

||||
|-|-|-|
|**檔案**|**用法**|**範例**|
|清除 .gif|用來呈現可折迭的區域||
|footer_slice .gif|頁尾簡報||
|info_icon .gif|顯示資訊時使用|免責聲明|
|online_icon .gif|此圖示要與線上連結相關聯||
|tabLeftBD .gif|用來呈現程式碼片段容器||
|tabRightBD .gif|用來呈現程式碼片段容器||
|vs_logo_bk .gif|用於標準對比標誌的參考，如 \<LogoFileName > 的商標 .xml 標記中所定義。  針對 Visual Studio 產品，標誌名稱是 vs_logo_bk .gif。||
|vs_logo_wh .gif|用於標準的高標誌參考，如商標 .xml 標記中所定義 \<LogoFileNameHC >。  針對 Visual Studio 產品，標誌名稱是 vs_logo_wh .gif。||
|ccOff .png|字幕圖形||
|ccOn .png|字幕圖形||
|ImageSprite .png|用來呈現可折迭的區域|展開或折迭圖形|

### <a name="deploying-a-set-of-topics"></a>部署一組主題
 這是一個簡單快速的教學課程，可讓您建立包含 .MSHA 檔案的「說明檢視器內容」部署集，以及包含主題的一組 cab 或 MSHCs。 .MSHA 是描述一組 cab 或 .MSHC 檔案的 XML 檔案。 說明檢視器可以讀取 .MSHA 來取得內容清單（。CAB 或.MSHC files）可供本機安裝。

 這只是描述說明檢視器 .MSHA 之非常基本 XML 架構的入門。  在這個簡短的總覽和範例 Helpcontentsetup.msha 底下，有一個範例的執行方式。 .msha。

 本入門的目的，.MSHA 的名稱是 Helpcontentsetup.msha. .msha （檔案的名稱可以是任何專案，副檔名為.MSHA）。 Helpcontentsetup.msha. .msha （以下範例）應該包含可用的計程車或 MSHCs 清單。  檔案類型在 .MSHA 內必須是一致的（不支援 .MSHA 和 CAB 檔案類型的組合）。 針對每個 CAB 或 .MSHC，應該會有一個 \<div class = "package" > ...\</div > （請參閱下面的範例）。

 注意：在下面的執行範例中，我們已包含商標套件。 為了取得所需的 Visual Studio 內容轉譯專案和內容行為，這是很重要的。

 範例 Helpcontentsetup.msha. .msha 檔案：（以您的檔案名取代「內容集名稱1」和「內容集名稱2」等）。

```
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.

```

1. 建立本機資料夾，例如 "C:\SampleContent"

2. 在此範例中，我們將使用 .MSHC 檔案來包含主題。  .MSHC 是 zip，副檔名從 .zip 變更為.MSHC.

3. 建立下列 Helpcontentsetup.msha 作為文字檔（用來建立檔案的 [記事本]），並將其儲存至上述資料夾（請參閱步驟1）。

   「商標」類別存在，而且是唯一的。 此入門中包含商標 .mshc，讓已安裝的內容具有商標，而包含在 MSHCs 中的內容行為將具有品牌套件中包含的適當支援元素。 如果沒有這種情況，當系統尋找不屬於已翻錄（已安裝）內容的支援專案時，將會產生錯誤。

   若要取得 Visual Studio 商標套件，請 Branding_en 將 C:\Program Files （x86） \Microsoft Help Viewer\v2.1\ 中的 .mshc 檔案複製到您的工作資料夾。

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>

```

 **摘要**

 使用和擴充上述步驟，可讓 Vsp 為 Visual Studio 說明檢視器部署其內容集。

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>將說明新增至 Visual Studio Shell （整合模式和獨立模式）
 **簡介**

 本逐步解說示範如何將說明內容併入 Visual Studio Shell 應用程式中，然後加以部署。

 **Requirements**

1. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]

2. [Visual Studio 2013 獨立模式 Shell 可轉散發套件](https://aka.ms/VS2013/IsoShell-LP/all)

   **概觀**

   [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Shell 是您可以用來作為應用程式基礎的 [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] IDE 版本。 這類應用程式包含獨立的 Shell，以及您所建立的擴充功能。 使用包含在 [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] SDK 中的獨立 Shell 專案範本來建立擴充功能。

   建立獨立的 Shell 型應用程式及其說明的基本步驟：

3. 取得 [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] ISO Shell 可轉散發套件（Microsoft 下載）。

4. 在 Visual Studio 中，建立以獨立模式 Shell 為基礎的說明延伸模組，例如本逐步解說稍後所述的 Contoso 說明延伸模組。

5. 將延伸模組和 ISO Shell 可轉散發套件包裝到部署 MSI （應用程式設定）。 此逐步解說不包含安裝步驟。

   建立 Visual Studio 內容存放區。 針對整合式 Shell 案例，請將 Visual Studio12 變更為產品目錄名稱，如下所示：

- 建立資料夾 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12。

- 建立名為 Catalogtype.xml 的檔案，並將它新增至資料夾。 檔案應該包含下列幾行程式碼：

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <catalogType>UserManaged</catalogType>
  ```

  定義登錄中的內容存放區。 針對整合式 Shell，請將 VisualStudio12 變更為產品目錄名稱：

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   索引鍵： LocationPath 字串值： C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-US

   索引鍵： CatalogName 字串值： [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] 檔

  **建立專案**

  若要建立獨立的 Shell 擴充功能：

1. 在 Visual Studio 的 [檔案]**底下，選擇**[**新增專案**]，在 **[** **其他專案類型**] 下選擇 [擴充性]，然後選擇 [ **Visual Studio Shell 隔離**]。 將專案命名為 `ContosoHelpShell`），以根據 Visual Studio 獨立模式 Shell 範本建立擴充性專案。

2. 在方案總管中，在 ContosoHelpShellUI 專案的 [資源檔] 資料夾中，開啟 System.windows.input.applicationcommands.paste .vsct。 請確定這一行已標記為批註（搜尋 "No_Help"）： `<!-- <define name=“No_HelpMenuCommands”/> -->`

3. 選擇 F5 鍵以編譯並執行**Debug**。 在獨立 Shell IDE 的實驗實例中，選擇 [說明 **] 功能表。** 請確定 [ **View**說明]、[**新增和移除說明內容**] 和 [設定說明**喜好設定**] 命令出現。

4. 在方案總管的 ContosHelpShell 專案中，于 [Shell 自訂] 資料夾中，開啟 ContosoHelpShell .pkgdef。 若要定義 Contoso 說明目錄，請新增下列幾行：

   ```
    [$RootKey$\Help]
   "Product"="Contoso"
   "Catalog"="Contoso"
   “Version"="100"
   "BrandingPackage"="ContosoBrandingPackage.mshc"
   ```

5. 在方案總管的 ContosHelpShell 專案中，于 [Shell 自訂] 資料夾中，開啟 ContosoHelpShell .pkgdef。 若要啟用 F1 說明，請新增下列幾行：

   ```
   // F1 Help Provider

   [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="13407"
   "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
   @="Help3 Provider"
   [$RootKey$\HelpProviders]
   @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
   [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="Help3 Provider"
   @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
   ```

6. 在方案總管中，在 ContosoHelpShell 方案的內容功能表上，選擇 [**屬性**] 功能表項目。 在 [設定**屬性**] 下，選取 [ **Configuration Manager**]。 在 [設定]**資料行中**，將每個 "Debug" 值變更為 "Release"。

7. 建置方案。 這會在發行資料夾中建立一組檔案，將在下一節中使用。

   若要測試這種情況，如同已部署：

8. 在您要部署 Contoso 的電腦上，安裝已下載的（從上方） ISO Shell。

9. 在 \\\Program Files （x86）\\中建立資料夾，並將它命名為 `Contoso`。

10. 將 ContosoHelpShell release 資料夾中的內容複寫到 \\\Program Files （x86） \Contoso\ 資料夾。

11. 在 [**開始**] 功能表中選擇 [**執行**]，然後輸入 `Regedit`，以啟動 [登錄編輯程式]。 在 [登錄編輯程式] 中 **，依序選擇 [** 檔案] 和 [匯**入**]。 流覽至 ContosoHelpShell 專案資料夾。 在 [ContosoHelpShell] 子資料夾中，選擇 [ContosoHelpShell]。

12. 建立內容存放區：

     針對 ISO Shell-建立 Contoso 內容存放區 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

     針對 [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] 整合式 Shell，建立資料夾 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12

13. 建立 Catalogtype.xml，並將新增至內容存放區（上一個步驟），其中包含：

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

14. 新增下列登錄機碼：

     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key： LocationPath 字串值：

     針對 ISO Shell：

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] 整合式 Shell：

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-US

     索引鍵： CatalogName 字串值： [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] 檔。 針對 ISO Shell，這是您的目錄名稱。

15. 將您的內容（cab 或 .MSHC 和 .MSHA）複製到本機資料夾。

16. 用於測試內容存放區的整合式 Shell 命令列範例。 針對 ISO Shell，適當地變更目錄和 launchingApp 值以符合產品。

      "C:\Program Files （x86） \Microsoft Help Viewer\v2.1\HlpViewer.exe"/catalogName VisualStudio12/helpQuery method = "page & id = ContosoTopic0"/launchingApp Microsoft，VisualStudio，12。0

17. 啟動 Contoso 應用程式（從 Contoso app 根目錄）。 在 [ISO Shell] 中，選擇 [說明 **] 功能表項目**，然後將 [**設定說明偏好**] 變更為 [**使用本機**說明]。

18. 在 shell 中，選擇 [說明 **] 功能表項目**，然後**參閱**[說明]。 本機說明檢視器應該會啟動。 選擇 [**管理內容**] 索引標籤。在 [**安裝來源**] 下，選擇 [**磁片**] 選項按鈕。 選擇 [ **...** ] 按鈕，然後流覽至包含 Contoso 內容的本機資料夾（複製到上一個步驟中的本機資料夾）。 選擇 [Helpcontentsetup.msha] .msha。 Contoso 現在應該會在書籍選擇中顯示為書籍。 選擇 [**新增**]，然後選擇 [**更新**] 按鈕（右下角）。

19. 在 Contoso IDE 中，選擇 F1 鍵來測試 F1 功能。

### <a name="additional-resources"></a>其他資源

如需執行時間 API，請參閱[Windows HELP API](https://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx)。

如需如何利用 Help API 的詳細資訊，請參閱說明[檢視器程式碼範例](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)。

如需重大問題的更新，請參閱說明[檢視器讀我檔案](https://go.microsoft.com/fwlink/?LinkId=255960)。
