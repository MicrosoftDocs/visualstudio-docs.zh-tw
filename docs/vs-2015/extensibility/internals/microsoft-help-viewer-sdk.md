---
title: Microsoft 說明檢視器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37512da136348a15792c11aae02bab9250c43670
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000896"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

這篇文章包含 Visual Studio 說明檢視器整合者的下列工作：

-   建立主題 （F1 支援）

-   建立 Help 檢視器內容品牌封裝

-   部署一份文件

-   新增 Visual Studio shell （整合模式或隔離） 說明

-   其他資源

### <a name="creating-a-topic-f1-support"></a>建立主題 （F1 支援）
 本節將提供的主題、 主題需求、 如何以其呈現的結果建立主題 （包括 F1 支援需求） 和最後，範例主題的簡短描述元件的概觀。

 **說明檢視器的主題概觀**

 呈現呼叫某個主題時，說明檢視器會取得與當時的安裝或最後一個更新，以及主題的 XHTML，主題相關聯的品牌封裝項目，並結合以產生呈現的內容檢視兩者 (商標資料 +主題資料）。  商標的套件中包含標誌、 支援內容的行為和商標文字 （著作權，等等）。  請參閱下方的品牌封裝元素的詳細資訊的 「 建立品牌封裝 」。  萬一沒有與主題相關聯的品牌封裝，說明檢視器會使用後援的品牌封裝位於說明檢視器應用程式根目錄 (Branding_en US.mshc)。

 **說明檢視器主題需求**

 若要在說明檢視器內正確轉譯，未經處理的主題內容必須是基本 1.1 XHTML W3C。

 主題通常包含兩個區段：

- 中繼資料 （請參閱內容的中繼資料參考）： 資料有關該主題，例如，主題的唯一識別碼，關鍵字值，目錄識別碼的主題父節點識別碼，依此類推。

- 本文內容： 符合 W3C 基本 1.1 XHTML，其中包含支援內容的行為 （可摺疊的區域、 程式碼片段等。完整清單如下所示）。

  Visual Studio 品牌封裝支援的控制項：

- 連結

- CodeSnippet

- CollapsibleArea

- 繼承的成員

- LanguageSpecificText

  受支援的語言字串 （不區分大小寫）：

- javascript

- csharp 或 c#

- cplusplus 或 visual c + + 或 c + +

- jscript

- visualbasic 或 vb

- f # fsharp 或 fs

- 其他 – 表示的語言名稱的字串

  **建立 Help Viewer 主題**

  建立新的 XHTML 文件，名為 ContosoTopic4.htm，並包含在 title 標記 （如下所示）。

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

 接下來，將資料加入至定義如何主題 （自我品牌與否），顯示如何參考本主題的 F1，本主題會在於目錄中，其識別碼 （適用於其他主題的連結參考），等等。請參閱 「 內容中繼資料 」 下表針對支援的中繼資料的完整清單。

- 在此情況下，我們將使用我們自己商標套件，Visual Studio 說明檢視器的品牌封裝的變數。

- 新增 F1 中繼名稱和值 ("Microsoft.Help.F1 」 內容 ="ContosoTopic4 」)，會比對 IDE 屬性包中提供的 F1 值。  （請參閱 [F1 支援] 區段，如需詳細資訊）。 這是對應到 F1 的值從 ide 即可顯示這個主題，在 IDE 中選擇 f1 鍵時所呼叫。

- 新增主題識別碼。 這是可由其他主題來連結至本主題的字串。  它是本主題說明檢視器識別碼。

- 針對目錄中，新增本主題的父節點，即可定義此主題的目錄節點會出現的位置。

- 針對目錄中，新增本主題的節點順序。 N 的數字的子系節點的父節點時，定義子節點順序本主題的位置。 例如，本主題是數字 4 的 4 子主題。)

  範例中繼資料 > 一節：

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

 **主題內文**

 （不包括頁首和頁尾） 中主題的主體會包含頁面的連結、 注意 > 一節、 可摺疊的區域、 程式碼片段中和一段特定文字的語言。  請參閱這些區域的相關主題的資訊呈現的商標設定區段。

1.  新增主題標題標記：  `<div class="title">Contoso Topic 4</div>`

2.  新增附註區段： `<div class="alert"> add your table tag and text </div>`

3.  新增可摺疊的區域：  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4.  加入程式碼片段：  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5.  新增程式碼的語言特定文字：`<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />`請注意該 devLangnu = 可讓您輸入其他語言。 比方說，devLangnu ="Fortran"會顯示 Fortran 時程式碼片段 DisplayLanguage = Fortran

6.  新增頁面的連結： `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
>  注意： 針對不受支援新的 「 顯示語言 」 (範例中， F#、 Cobol、 Fortran) 程式碼顏色標示程式碼片段中的將會是單色。

 **範例說明檢視器主題**的程式碼說明如何定義中繼資料、 程式碼片段、 可摺疊的區域和語言特定的文字。

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

 在 Visual Studio 中，選取 F1 會產生從 IDE 中的資料指標位置所提供的值並於其中填入 「 屬性包 」 與提供的值 （根據游標位置。 當游標位於功能 x 時，x 功能是在主動/焦點，並填入值的屬性包。  選取 f1 鍵時的屬性包會填入和 Visual Studio F1 程式碼看起來的客戶預設說明來源是否為本機或在線上 （online 是預設值），然後建立適當的字串，根據設定的使用者 （online 是預設值） – 殼層執行（請參閱協助系統管理員指南 exe 啟動參數） 的本機說明檢視器再加上關鍵字，從屬性包，如果本機說明的預設值或參數清單中的關鍵字將 MSDN URL 的參數。

 如果三個字串所傳回的 f1 鍵，參考為多重值字串時，需要在第一個詞彙，尋找叫用，如果找不到，我們已完成; 和否則，請移至下一個字串。  順序很重要。 多重值關鍵字的呈現方式應該是最長的字串，以最短的字串。  若要確認如果是多重值的關鍵字，看看線上 F1 URL 字串，其中包含所選的關鍵字。

 在 Visual Studio 2012 中，我們刻意之間所做更強的除以線上和離線，以便針對 Online 使用者的設定時，然後我們只是 F1 要求直接傳遞至我們的線上查詢服務於 MSDN，而不是協助程式庫代理程式透過路由我們必須在 Visual Studio 2010。 我們再仰賴的狀態為 「 廠商已安裝的內容 = true"來判斷是否有不同的內容中。 如果為 true，我們再執行此剖析和路由邏輯取決於您想要為您的客戶支援。 如果為 false，則我們只要移至 MSDN。 如果使用者的設定是本機，然後移至本機說明引擎的所有呼叫。

 F1 流程圖表：

 ![F1 流程](../../extensibility/internals/media/f1flow.png "F1flow")

 當說明檢視器的預設說明內容來源設定為線上 （啟動瀏覽器中）：

- Visual Studio 合作夥伴 (VSP) 功能發出 F1 屬性包 （屬性包 prefix.keyword 和線上 URL 在登錄中找到的前置詞） 的值： F1 傳送 VSP URL + 參數至瀏覽器。

- Visual Studio 功能 （語言編輯器，Visual Studio 特定的功能表項目等）： F1 將 Visual Studio URL 傳送給瀏覽器。

  當說明檢視器的預設說明內容來源設定為本機說明 （Help Viewer 中啟動）：

- F1 屬性包與本機存放區索引之間的關鍵字相符的 VSP 功能 (也就是屬性包 prefix.keyword = 本機存放區索引中找到的值): F1 呈現說明檢視器中的主題。

- Visual Studio 功能 （沒有的選項來覆寫所發出的 Visual Studio 功能的屬性包 VSP）： F1 呈現 Visual Studio 中的主題說明檢視器。

  設定下列登錄值以啟用 F1 後援廠商說明內容。 F1 後援表示線上說明檢視器設定為尋找 F1 說明內容，而且廠商內容會在本機安裝到使用者的硬碟機。 說明檢視器應該查看本機說明內容，即使預設設定是取得線上說明。

1. 設定**VendorContent**說明 2.1 登錄機碼下的值：

   -   適用於 32 位元作業系統：

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        「 VendorContent"= dword: 00000001

   -   適用於 64 位元作業系統：

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        「 VendorContent"= dword: 00000001

2. 註冊說明 2.1 登錄機碼的夥伴命名空間：

   - 適用於 32 位元作業系統：

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Partner<em>\\< 命名空間\></em>

      「 位置 」 = 「 離線 」

   - 適用於 64 位元作業系統：

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Partner<em>\\< 命名空間\></em>

      「 位置 」 = 「 離線 」

   **剖析的基底原生命名空間**

   若要開啟基底的原生命名空間剖析，在登錄中新增 DWORD 的名稱： BaseNativeNamespaces 並設定其值為 1 （下他們想要支援目錄索引鍵）。  例如，如果您想要使用 Visual Studio 類別目錄，您無法將金鑰新增至路徑：

   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   當標頭/方法時發現格式 F1 關鍵字時，'/' 字元將會被剖析，導致下列建構：

- 標頭： 將會是可用來在登錄中登錄的命名空間

- 方法： 這會成為傳遞的關鍵字。

  例如，假設一個稱為 CustomLibrary 的自訂程式庫和方法，稱為 MyTestMethod，當要求傳入 F1 將會格式化為`CustomLibrary/MyTestMethod`。

  使用者可以註冊 CustomLibrary 為命名空間底下的合作夥伴，並提供他們想要的任何位置索引鍵，因此傳遞給查詢的關鍵字 MyTestMethod。

  **啟用偵錯工具在 IDE 中的說明**

  新增下列登錄機碼和值：

  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\Dynamic 說明鍵： 零售值中的 顯示偵錯輸出: 是

  在 IDE 中，[說明] 功能表項目之下，選取 [偵錯協助內容]

  **內容的中繼資料**

  在下表中，括號之間出現的任何字串會是一個預留位置，必須可辨識的值來取代。 例如，在\<中繼 name="Microsoft.Help.Locale"內容 ="在 [語言]"/ >，"[語言程式碼]"必須取代的值，例如 「 en-us-我們"。

|屬性 （HTML 表示）|描述|
|--------------------------------------|-----------------|
|\< 中繼 name="Microsoft.Help.Locale"內容 ="[語言代碼]"/ >|本主題的地區設定。 如果此標記用在主題中，必須一次使用，而且它必須插入上述任何其他的 Microsoft 說明標記。 如果未使用此標記，本主題的內文會使用斷詞工具所關聯的產品地區設定中，如果您指定了; 編製索引否則，en-us-我們會使用斷詞工具。 ISOC RFC 4646 符合此標記。 若要確保 Microsoft 技術能夠正常運作，使用此屬性而不是一般的 [語言] 屬性。|
|\< 中繼 name="Microsoft.Help.TopicLocale"內容 ="[語言代碼]"/ >|本主題的地區設定時也會使用其他地區設定。 如果此標記用在主題中，它必須使用一次。 當類別目錄包含在一個以上的語言中的內容時，請使用這個標記。 在目錄中的多個主題可以有相同的識別碼，但必須指定唯一的 TopicLocale 的每個。 指定符合目錄的地區設定 TopicLocale 主題是顯示在目錄中的主題。 不過，本主題的所有語言版本會都顯示在搜尋結果中。|
|\< 標題 > [標題] \< /標題 >|指定本主題的標題。 此標記為必要項，並必須用於主題的一次。 如果本主題的本文不包含標題\<d i v > 區段中，這個標題會顯示主題中，並在目錄中。|
|\< 中繼名稱 ="Microsoft.Help.Keywords 」 內容 ="[aKeywordPhrase]"/ >|指定連結的說明檢視器的 [索引] 窗格中顯示的文字。 按一下連結時，即會顯示主題。您可以指定多個索引關鍵字的主題，或如果您不想要顯示在索引中此主題的連結，您可以省略此標記。 "K"關鍵字，從早期版本的說明可以轉換成這個屬性。|
|\< 中繼 name="Microsoft.Help.Id"內容 ="[TopicID]"/ >|設定本主題的識別碼。 此標記為必要項，並必須用於主題的一次。 識別碼必須是唯一的目錄中有相同的地區設定的主題。 在另一個主題中，您可以建立本主題的連結，使用此識別碼。|
|\< 中繼 name="Microsoft.Help.F1"content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|指定本主題的 f1 說明關鍵字。 您可以指定多個 F1 關鍵字的主題，或如果不想讓此應用程式使用者按下 F1 鍵時要顯示的主題，您可以省略此標記。 通常，只有一個 F1 關鍵字會指定主題。 "F"關鍵字，從早期版本的說明可以轉換成這個屬性。|
|\< 中繼名稱 ="Description"content ="[主題 description]"/ >|提供簡短摘要，本主題中的內容。 如果此標記用在主題中，它必須使用一次。 直接由查詢程式庫，存取這個屬性它不會儲存在索引檔案。|
 中繼 name="Microsoft.Help.TocParent"內容 ="[sys.internal_tables]"/ >|指定本主題的最上層主題中的目錄。 此標記為必要項，並必須用於主題的一次。 這個值會是父代的 Microsoft.Help.Id。 主題可以有一個位置資料表中的內容。 "-1"，就會被視為目錄根的主題識別碼。 在  [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]，該頁面是說明檢視器首頁。 這是我們特別將 TocParent = 1 加入一些主題，以確保，它們會顯示在上方層級相同的原因。說明檢視器首頁是系統頁面，因此不可取代。 如果 VSP 嘗試新增的頁面識別碼為-1 時，它可能會加入至內容集，但說明檢視器一律會使用 系統 頁面-說明檢視器首頁|
|\< 中繼 name="Microsoft.Help.TocOrder"內容 ="[整數]"/ >|指定的目錄中本主題出現的位置相對於其對等主題。 此標記為必要項，並必須用於主題的一次。 值為整數。 指定的數值較小的整數的主題上方指定較高值整數的主題。|
|\< 中繼 name="Microsoft.Help.Product"內容 ="[product code]"/ >|指定此主題描述的產品。 如果此標記用在主題中，它必須使用一次。 這項資訊也可做為參數傳遞給協助索引子。|
|\< 中繼 name="Microsoft.Help.ProductVersion"內容 ="[版本號碼]"/ >|指定此主題描述的產品版本。 如果此標記用在主題中，它必須使用一次。 這項資訊也可做為參數傳遞給協助索引子。|
|\< 中繼 name="Microsoft.Help.Category"內容 ="[string]"/ >|用來識別小節內容的產品。 您可以識別多個小節的主題，或如果您不想找出任何小節的連結，您可以省略此標記。 此標記用來儲存 TargetOS 和 TargetFrameworkMoniker 的屬性，當轉換從較早版本的說明主題。 內容的格式是 AttributeName:AttributeValue。|
|\< 中繼 name="Microsoft.Help.TopicVersion 內容 ="[主題版本號碼]"/ >|在目錄中的多個版本存在時，請指定此版本的主題。 Microsoft.Help.Id 不保證是唯一的因為此標記時，需要多個版本的主題時存在，在目錄中，例如，目錄包含.NET Framework 3.5 和主題的主題，適用於.NET Framework 4 而且兩者都有相同的 Micro軟性。Help.Id。|
|\< 中繼名稱 ="SelfBranded"content ="[為 TRUE 或 FALSE]"/ >|指定本主題使用 Help Library 管理員啟動商標或商標套件的特定主題。 此標記必須是 TRUE 或 FALSE。 如果是 TRUE，則相關主題的品牌封裝會覆寫 Help Library 管理員啟動，以便讓主題呈現如預期般，即使其不同於其他內容的轉譯時，會設定品牌封裝。 如果是 FALSE，目前的主題是根據 Help Library 管理員啟動時設定品牌封裝中呈現。 根據預設，Help Library 管理員假設自我品牌除非 SelfBranded 變數宣告為 TRUE; 否則為 false因此，您並不需要宣告\<中繼名稱 ="SelfBranded"content ="FALSE"/ >。|

### <a name="creating-a-branding-package"></a>建立品牌封裝
 Visual Studio 版本包含幾個不同的 Visual Studio 產品，包括適用於 Visual Studio 合作夥伴的隔離和整合式的 shell。  每個這些產品都需要某種程度的主題為基礎說明內容的支援，唯一產品的商標。  例如，Visual Studio 主題需要有一致的品牌的簡報，而 SQL Studio，包裝 ISO Shell，則需要使用它自己唯一說明內容的商標每個主題。  整合式 Shell 合作夥伴可能會想要能在 Visual Studio 產品的說明內容的父系，同時維持自己的主題商標其 [說明] 主題。

 安裝商標套件，其中包含說明檢視器的產品。  適用於 Visual Studio 產品：

- 後援的品牌封裝 (Branding_\<地區設定 >.mshc) 安裝說明檢視器 2.1 應用程式根目錄中 (範例： C:\Program Files (x86) \Microsoft Help Viewer\v2.1) 說明檢視器語言組件。  這適用於未安裝任一產品品牌封裝的情況下 （已安裝任何內容） 或已安裝的品牌封裝已損毀的位置。  使用應用程式根後援品牌封裝時，會忽略的 Visual Studio 項目 （標誌和意見反應）。

- Visual Studio 內容安裝時從內容套件服務，品牌封裝也會安裝 （適用於第一個時間內容的安裝案例）。  品牌封裝更新時下, 一步 的內容更新或其他封裝安裝動作發生時，就是會安裝的更新。

  Microsoft Help Viewer 支援主題的主題中繼資料的商標。

- 主題的中繼資料其中定義自我品牌 = true、 呈現主題現狀，不執行任何動作 （而言商標）。

- 主題的中繼資料其中定義自我品牌 = false，使用商標套件 TopicVendor 中繼資料值相關聯。

- 其中主題中繼資料定義 name="Microsoft.Help.TopicVendor"內容 =\<廠商 MSHA 中的品牌封裝名稱 >，使用商標套件中的內容值定義。

- 在 Visual Studio 類別目錄中沒有的品牌封裝的優先順序應用程式。  套用第一個 Visual Studio 預設商標時，，然後如果主題中繼資料中定義，且支援 （如安裝 msha 中所定義） 相關聯的品牌封裝，廠商定義商標套用覆寫。

  品牌元素通常可分為三個主要類別：

- （範例包括意見反應 連結、 條件式免責聲明文字、 標誌） 的標頭項目

- 內容行為 （範例包括展開/摺疊控制項文字的項目及程式碼片段項目）

- 頁尾項目 （例如著作權）

  視為加上品牌的項目包含的項目 （此規格中詳述）：

- 目錄/產品標誌 （例如，Visual Studio）

- 意見反應連結和電子郵件項目

- 套用免責聲明文字

- 著作權的文字

  在 Visual Studio 說明檢視器的品牌封裝中支援的檔案包括：

- （標誌、 圖示等） 的圖形

- Branding.js – 指令碼檔案支援內容的行為

- Branding.xml – 一致地用於目錄內容的字串。  注意： Visual Studio 的當地語系化文字項目中 branding.xml，包括 _locID ="\<唯一的值 > 」

- Branding.css – 簡報一致性的樣式定義

- Printing.css – 一致的列印呈現的樣式定義

  如先前所述，品牌封裝是與主題相關聯：

- 當 SelfBranded = false 已定義的中繼資料中，主題會繼承目錄的品牌封裝

- 或當 SelfBranded = false 和那里獨特的品牌封裝定義於 MSHA 與可用時安裝內容

  針對實作自訂的品牌封裝的 Vsp (VSP 內容，SelfBranded = True)，繼續執行的一種方法是啟動與後援的品牌封裝 （安裝說明檢視器），並變更適當的檔案名稱。  Branding_\<地區設定 >.mshc 檔案會變更為.mshc 檔案副檔名的 zip 檔案，因此只要將副檔名從.mshc 變更為.zip 和將內容解壓縮。  請參閱以下的品牌封裝元素，並修改視需要 （例如，VSP 商標和標誌 Branding.xml 檔案中參考變更標誌、 每 VSP 細節等更新 Branding.xml）。

  完成所有修改，請建立包含所需的品牌元素的 zip 檔案，並將副檔名變更為.mshc。

  若要建立關聯的自訂商標套件，請建立 MSHA，其中包含商標 mshc 檔案以及內容的 mshc （其中包含的主題） 的參考。  請參閱以下 「 MSHA 「 如何建立基本的 MSHA。

  Branding.xml 檔案包含用於以一致的方式呈現在主題中的特定項目，當主題包含清單項目\<中繼 name="Microsoft.Help.SelfBranded"內容 ="false"/ >。  Visual Studio 清單 Branding.xml 檔案中的項目如下所示。  這份清單被要用作需要 ISO Shell 採用者，他們用來修改這些項目 （例如標誌、 意見反應和著作權） 以符合他們自己的產品品牌的範本。

  注意： 記下的"{n}"的變數具有程式碼相依性，移除或變更這些值會導致錯誤和可能的應用程式當機。Visual Studio 品牌封裝中包含當地語系化的識別項 (範例 _locID="codesnippet.n")。

  **Branding.xml**

|||
|-|-|
|功能：|**CollapsibleArea**|
|用法:|展開摺疊內容控制項文字|
|**目**|**值**|
|ExpandText|Expand|
|CollapseText|摺疊|
|功能：|**CodeSnippet**|
|用法:|程式碼片段控制項文字。  注意: 「 非中斷 」 空間的程式碼片段內容將會變更至空間。|
|**目**|**值**|
|CopyToClipboard|複製至剪貼簿|
|ViewColorizedText|檢視彩色樣式|
|CombinedVBTabDisplayLanguage|Visual Basic （範例）|
|VBDeclaration|宣告|
|VBUsage|使用量|
|功能：|**意見反應、 頁尾和標誌**|
|用法:|提供客戶提供有關透過電子郵件的目前主題的意見反應的意見反應控制項。  著作權文字內容。  標誌的定義。|
|**目**|**值 （這些字串可以修改以符合內容的採用者需要）。**|
|著作權|© 2013 Microsoft Corporation。 著作權所有，並保留一切權利。|
|SendFeedback|\<a ="{0}」 {1}> 傳送意見反應 \< /a > 給 Microsoft 的這個主題。|
|FeedbackLink||
|LogoTitle|[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]|
|LogoFileName|vs_logo_bk.gif|
|LogoFileNameHC|vs_logo_wh.gif|
|功能：|**免責聲明**|
|用法:|一組機器案例特定的免責聲明的翻譯內容。|
|**目**|**值**|
|MT_Editable|本文是機器翻譯。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|
|MT_NonEditable|本文是機器翻譯。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|
|MT_QualityEditable|本文是人工翻譯。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|
|MT_QualityNonEditable|本文是人工翻譯。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|
|MT_BetaContents|這篇文章是針對初步發行的機器翻譯。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|
|MT_BetaRecycledContents|本文是人工翻譯為初步發行版。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|
|功能：|**用於 LinkTable**|
|用法:|如需線上主題的連結支援|
|**目**|**值**|
|LinkTableTitle|連結資料表|
|TopicEnuLinkText|檢視的英文版 \< /a > 您的電腦上可以使用本主題。|
|TopicOnlineLinkText|檢視這個主題\<href ="{0}" {1}> online \< /a >|
|OnlineText|Online|
|功能：|**視訊的音訊控制項**|
|用法:|顯示項目和視訊內容的文字|
|**目**|**值**|
|MultiMediaNotSupported|Internet Explorer 9 或更新版本必須安裝支援{0}內容。|
|VideoText|顯示視訊|
|AudioText|資料流處理音訊|
|OnlineVideoLinkText|\<p > 若要檢視與這個主題相關的影片，請按一下{0} \<href ="{1}">{2}這裡\</a >。\</ p >|
|OnlineAudioLinkText|\<p > 若要聆聽與這個主題相關聯的音訊，按一下{0} \<href ="{1}">{2}這裡\</a >。\</ p >|
|功能：|**未安裝的內容控制項**|
|用法:|用於 contentnotinstalled.htm 轉譯的文字元素 （字串）|
|**目**|**值**|
|ContentNotInstalledTitle|在您的電腦上找不到任何內容。|
|ContentNotInstalledDownloadContentText|\<p > 若要將內容下載到您的電腦， \<href ="{0}" {1}> 按一下 [管理] 索引標籤\</a >。\</ p >|
|ContentNotInstalledText|\<p > 您的電腦上已安裝的任何內容。 請參閱您的系統管理員的本機說明內容安裝。 \< /p >|
|功能：|**主題找不到控制項**|
|用法:|用於 topicnotfound.htm 轉譯的文字元素 （字串）|
|**目**|**值**|
|TopicNotFoundTitle|在您的電腦上找不到要求的主題。|
|TopicNotFoundViewOnlineText|\<p > 您的電腦上找不到所要求的主題，但是您可以\<href ="{0}" {1}> 檢視線上主題\</a >。\</ p >|
|TopicNotFoundDownloadContentText|\<p > 查看類似的主題，連結的瀏覽窗格或\<href ="{0}" {1}> 按一下 [管理] 索引標籤\</a > 為內容下載到您的電腦。\</ p >|
|TopicNotFoundText|\<p > 您的電腦上找不到所要求的主題。 \< /p >|
|功能：|**主題已損毀的控制項**|
|用法:|用於 topiccorrupted.htm 轉譯的文字元素 （字串）|
|**目**|**值**|
|TopicCorruptedTitle|無法顯示要求的主題。|
|TopicCorruptedViewOnlineText|\<p > 說明檢視器會無法顯示要求的主題。 可能有錯誤主題的內容或基礎系統相依性。 \< /p >|
|功能：|**首頁上的控制項**|
|用法:|支援說明檢視器的最上層節點內容的顯示文字。|
|**目**|**值**|
|HomePageTitle|說明檢視器首頁|
|HomePageIntroduction|\<p > 歡迎使用 Microsoft Help Viewer，基本每一位使用者使用 Microsoft 工具、 產品、 技術和服務的資訊來源。 說明檢視器可讓您存取使用說明及參考資訊、 範例程式碼、 技術文章等等。 若要尋找的需要請瀏覽目錄的內容，使用全文檢索搜尋，或瀏覽使用關鍵字索引的內容。 \< /p >|
|HomePageContentInstallText|\<p >\<b / > 使用\<href ="{0}" {1}> 管理內容\</a > 索引標籤上，執行下列動作：\<u l >\<l i > 將內容新增至您的電腦。\</ l i >\<l i > 檢查您的本機內容的更新。\</ l i >\<l i > 移除您的電腦上的內容。\</ l i >\</u l > \< /p >|
|HomePageInstalledBooks|已安裝的書籍|
|HomePageNoBooksInstalled|在您的電腦上找不到任何內容。|
|HomePageHelpSettings|說明內容設定|
|HomePageHelpSettingsText|\<p > 您目前的設定是本機說明。 說明檢視器會顯示您已安裝在電腦的內容。\<b / > 若要變更您的來源的說明內容，請在 Visual Studio 功能表列上選擇\<s p a n style ="{0}"> 協助，請設定說明偏好\</s p a n >。\<b / > \< /p >|
|Mb|MB|

 **branding.js**

 Branding.js 檔案包含 Visual Studio 說明檢視器的品牌元素所使用的 JavaScript。  以下是品牌元素和支援的 JavaScript 函式的清單。  這個檔案是當地語系化的所有字串是區段中都定義 「 可當地語系化的字串"這個檔案的頂端。  已建立 ICL 檔案 branding.js 檔案內當地語系化字串。

||||
|-|-|-|
|**商標功能**|**JavaScript 函式**|**描述**|
|Var...||定義變數|
|取得使用者程式碼語言|setUserPreferenceLang|對應索引 # 程式碼語言|
|設定和取得 cookie 值|getCookie setCookie||
|繼承的成員|changeMembersLabel|展開/摺疊繼承的成員|
|當 SelfBranded = False|onLoad|讀取查詢字串來檢查其是否為列印要求。  設定將使用者的慣用索引標籤的所有 codesnippets。如果是列印要求，然後設定 isPrinterFriendly 為 true。 檢查有高對比模式。|
|程式碼片段|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|在清單中撰寫所有的可摺疊的控制項物件。|
||CA_Click|可摺疊的區域狀態為基礎，定義哪些映像和呈現的文字|
|標誌的對比支援|isBlackBackground()|呼叫以判斷這是否為黑色背景。  精確時，才在高對比模式中。|
||isHighContrast()|使用色彩的範圍來偵測高對比模式|
||onHighContrast(black)|當偵測到高對比時呼叫|
|LST 功能|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|多媒體功能|標題 （開始、 結束時，文字樣式）||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify （styleName、 styleValue）||
||showCC(id)||
||subtitle(id)||

 **HTM 檔案**

 品牌封裝包含一組支援的通訊金鑰資訊，以便說明內容的使用者，例如首頁，其中包含描述安裝哪些內容集的區段和頁面時主題無法告知使用者案例的 HTM 檔案位於本機的主題集。 每項產品，您可以修改這些 HTM 檔案。  ISO Shell 廠商可採取的預設商標套件，並將行為和這些頁面的內容套件自己的需求。  這些檔案會參考其相對應的商標套件，才能將商標的標記，以取得從 branding.xml 檔案的相對應的內容中。

||||
|-|-|-|
|**檔案**|**使用**|**顯示內容的來源**|
|homepage.htm|這是頁面會顯示目前已安裝的內容，以及適當呈現給使用者，其內容相關的任何其他訊息。  此檔案具有額外的中繼資料屬性 」 Microsoft.Help.Id"內容 ="-1"，而放置此內容在本機內容目錄的頂端。||
||&LT; META_HOME_PAGE_TITLE_ADD / &GT;|Branding.xml、 標記\<HomePageTitle >|
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.xml、 標記\<HomePageIntroduction >|
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / &GT;|Branding.xml、 標記\<HomePageContentInstallText >|
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|標題區段 Branding.xml 標記\<HomePageInstalledBooks >，從應用程式，產生的資料\<HomePageNoBooksInstalled > 何時安裝任何書。|
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|標題區段 Branding.xml 標記\<HomePageHelpSettings >，區段文字\<HomePageHelpSettingsText >。|
|topiccorrupted.htm|當本機集合中的主題存在，但無法顯示因為某些原因 （損毀的內容）。||
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.xml、 標記\<TopicCorruptedTitle >|
||&LT; TOPIC_CORRUPTED_SECTION_ADD / &GT;|Branding.xml、 標記\<TopicCorruptedViewOnlineText >|
|topicnotfound.htm|當主題找不到本機內容中設定，也無法再使用 online||
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD / &GT;|Branding.xml、 標記\<TopicNotFoundTitle >|
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.xml、 標記\<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.xml、 標記\<TopicNotFoundText >|
|contentnotinstalled.htm|當沒有本機安裝之產品的內容。||
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD / &GT;|Branding.xml、 標記\<ContentNotInstalledTitle >|
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD / &GT;|Branding.xml、 標記\<ContentNotInstalledDownloadContentText >|
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD / &GT;|Branding.xml、 標記\<ContentNotInstalledText >|

 **CSS 檔案**

 Visual Studio 說明檢視器品牌封裝包含兩個的 css 檔案，以支援一致的 Visual Studio 說明內容呈現：

- Branding.css – 包含 css 項目呈現位置 SelfBranded = false

- Printer.css – 包含 css 項目呈現位置 SelfBranded = false

  Branding.css 檔案包含 Visual Studio 主題簡報的定義 (需要注意的是 branding.css 內 Branding_\<地區設定 >.mshc 從封裝服務可能會變更)。

  **圖形檔**

  Visual Studio 標誌，以及其他圖形，則會顯示 visual Studio 內容。  Visual Studio 說明檢視器的品牌封裝中的圖形檔案的完整清單如下所示。

||||
|-|-|-|
|**檔案**|**使用**|**範例**|
|clear.gif|用來呈現可摺疊區域||
|footer_slice.gif|頁尾簡報||
|info_icon.gif|用來顯示資訊|免責聲明|
|online_icon.gif|此圖示會與線上連結相關聯||
|tabLeftBD.gif|用來呈現程式碼片段容器||
|tabRightBD.gif|用來呈現程式碼片段容器||
|vs_logo_bk.gif|Branding.xml 標記中所定義，用於一般的對比標誌參考\<LogoFileName >。  適用於 Visual Studio 產品標誌名稱會是 vs_logo_bk.gif。||
|vs_logo_wh.gif|用於 Branding.xml 標記中所定義的一般高標誌參考\<LogoFileNameHC >。  適用於 Visual Studio 產品標誌名稱會是 vs_logo_wh.gif。||
|ccOff.png|隱藏式輔助字幕的圖形||
|ccOn.png|隱藏式輔助字幕的圖形||
|ImageSprite.png|用來呈現可摺疊區域|展開或摺疊圖形|

### <a name="deploying-a-set-of-topics"></a>部署一組的主題
 這是簡單且快速的教學課程，建立說明檢視器內容部署集 MSHA 檔案及 cab 或其中包含主題的 MSHCs 組所組成。 描述一組的 cab 檔案的 XML 檔案或 MSHC 檔案 MSHA。 說明檢視器可以讀取以取得一份內容 (MSHA。封包或。MSHC 檔案） 可供本機安裝。

 這是只描述非常基本的 XML 結構描述的說明檢視器 MSHA 入門指南。  沒有這個簡短的概觀和範例 HelpContentSetup.msha 下方的範例實作。

 此入門，目的 MSHA，名稱是的 HelpContentSetup.msha （檔案名稱可以是任何項目，擴充功能。MSHA)。 HelpContentSetup.msha （下面的範例） 應該包含一份 cab 或 MSHCs 可用。  檔案類型必須是內 （不支援 MSHA 和 CAB 檔案類型的組合） MSHA 保持一致。 針對每個封包或 MSHC，應該會有\<div 類別 ="套件">...\</div > （請參閱以下範例）。

 注意： 在實作範例中中,，我們都納入商標的套件。 這很重要的包含，以便取得所需的 Visual Studio 內容呈現項目和內容的行為。

 範例 [HelpContentSetup.msha] 檔案: (取代 「 內容會設定名稱 1 」 和 「 內容集名稱 2 」 等等，都是與您的檔案名稱。)

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

1. 建立本機資料夾，如下所示"C:\SampleContent 」

2. 此範例中，我們將使用 MSHC 檔案包含的主題。  MSHC 會變更以.zip 副檔名的 zip。MSHC。

3. 建立以下 HelpContentSetup.msha 為文字檔案 （用於 「 記事本 」 建立的檔案） 並將它儲存到上述的記下資料夾 （請參閱步驟 1）。

   類別 「 商標 」 存在，而且是唯一的。 商標 mshc 一併併入此入門，以便安裝的內容會有商標和 MSHCs 中所包含內容的行為會有商標的套件中包含適當的支援項目。 如果沒有這麼做，系統會尋找不屬於擷取的 （安裝） 的支援項目的內容時，會產生錯誤。

   若要取得 Visual Studio 品牌封裝，將 Branding_en US.mshc 檔案位於 C:\Program Files (x86) \Microsoft Help Viewer\v2.1\ 複製到您的工作資料夾。

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

 使用及延伸上述的步驟可讓 Vsp 來部署 Visual Studio 說明檢視器及其內容的集合。

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>將說明加入至 Visual Studio Shell （整合模式和獨立模式）
 **簡介**

 本逐步解說示範如何併入 Visual Studio Shell 應用程式中的說明內容，然後再加以部署。

 **需求**

1. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]

2. [Visual Studio 2013 獨立模式 Shell 可轉散發套件](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)

   **概觀**

   [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]殼層是一份[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]IDE，您可以根據應用程式。 這類應用程式包含您所建立的延伸模組以及 Isolated Shell。 使用獨立 Shell 專案範本，其中包含在[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]SDK 來建置擴充功能。

   建立獨立模式 Shell 為基礎的應用程式和其說明的基本步驟：

3. 取得[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]ISO Shell 可轉散發套件 （Microsoft 下載）。

4. 在 Visual Studio 中，建立說明延伸模組為基礎的隔離 Shell 中，例如，本逐步解說稍後所述的 Contoso 說明延伸模組。

5. 換行的擴充功能與 ISO Shell 可轉散發到部署 MSI （應用程式安裝程式）。 本逐步解說不包括設定步驟。

   建立 Visual Studio 內容存放區。 整合式 Shell 案例中，變更視覺化 Studio12 產品類別目錄名稱，如下所示：

- 建立資料夾 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12。

- 建立名為 CatalogType.xml 檔案，並將它新增至資料夾。 此檔案應包含下列程式碼行：

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <catalogType>UserManaged</catalogType>
  ```

  在登錄中定義的內容存放區。 整合式 Shell 中，變更 VisualStudio12 中產品類別目錄名稱的內容︰

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   索引鍵： LocationPath 字串值： C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-US

   索引鍵： CatalogName 字串值：[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]文件

  **建立專案**

  若要建立獨立模式 Shell 擴充功能：

1. 在 Visual Studio 中下,**檔案**，選擇**新增專案**下方**其他專案類型**選擇**擴充性**，然後選擇  **Visual Studio Shell 隔離**。 將專案命名為`ContosoHelpShell`) 來建立 Visual Studio Isolated Shell 範本為基礎的擴充性專案。

2. 在 [方案總管] 中，在 ContosoHelpShellUI 專案中，在資源檔的資料夾中，開啟 ApplicationCommands.vsct。 請確定這一行標記為註解 （搜尋"No_Help"）： `<!-- <define name=“No_HelpMenuCommands”/> -->`

3. 選擇 F5 鍵以編譯並執行**偵錯**。 在隔離的殼層 IDE 的實驗性執行個體，選擇**協助**功能表。 請確定**檢視有助於**，**新增和移除說明內容**，和**設定說明偏好**命令會顯示。

4. 在 [方案總管] 中，在 ContosHelpShell 專案中，在 Shell 自訂資料夾中，開啟 ContosoHelpShell.pkgdef。 若要定義 Contoso 說明目錄，新增下列幾行：

   ```
    [$RootKey$\Help]
   "Product"="Contoso"
   "Catalog"="Contoso"
   “Version"="100"
   "BrandingPackage"="ContosoBrandingPackage.mshc"
   ```

5. 在 [方案總管] 中，在 ContosHelpShell 專案中，在 Shell 自訂資料夾中，開啟 ContosoHelpShell.Application.pkgdef。 若要啟用 F1 說明，請新增下列幾行：

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

6. 在 方案總管的 ContosoHelpShell 方案時，操作功能表上選擇**屬性**功能表項目。 底下**組態屬性**，選取**Configuration Manager**。 在 [**組態**] 欄中，將每個 「 偵錯 」 的值變更為 「 發行 」。

7. 建置方案。 這會建立一組檔案發行資料夾，將用於下一節。

   若要測試這個，如同部署：

8. 在電腦上，您要部署 Contoso，若要安裝下載的 ISO 殼層 （上述）。

9. 建立資料夾\\\Program Files (x86)\\，並將它命名`Contoso`。

10. 內容複製到 ContosoHelpShell 發行資料夾\\\Program Files (x86) \Contoso\ 資料夾。

11. 啟動登錄編輯程式選擇**執行**中**開始**功能表，然後輸入`Regedit`。 在 登錄編輯器中，選擇**檔案**，然後**匯入**。 瀏覽至 ContosoHelpShell 專案資料夾。 在 ContosoHelpShell 子資料夾中，選擇 ContosoHelpShell.reg。

12. 建立內容的存放區：

     ISO shell-建立 Contoso 內容存放區 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

     針對[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]整合式 Shell、 建立資料夾 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12

13. 建立 CatalogType.xml 並加入要包含的內容存放區 （上一個步驟）：

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

14. 新增下列登錄機碼：

     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key: LocationPath 字串值：

     ISO shell:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] 整合式的 Shell:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-美國

     索引鍵： CatalogName 字串值：[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]文件。 ISO 殼層，這是您目錄的名稱。

15. 將您的內容 （cab 或 MSHC 和 MSHA） 複製到本機資料夾。

16. 整合式 Shell 命令列範例測試內容存放區。 ISO shell 變更類別目錄和 launchingApp 為適當的值來比對的產品。

      "C:\Program 檔案 (x86) \Microsoft Help Viewer\v2.1\HlpViewer.exe"/catalogName VisualStudio12 /helpQuery 方法 = 「 頁面 」 與 「 識別碼 = ContosoTopic0"/launchingApp Microsoft VisualStudio，12.0

17. 啟動 Contoso 應用程式 （來自 Contoso 應用程式根目錄中）。 在 ISO Shell 中，選擇**幫助**功能表項目，以及變更**設定說明偏好**來**使用本機說明**。

18. 在殼層中，選擇**幫助**功能表項目，然後**檢視說明**。 本機說明檢視器應會啟動。 選擇 [管理內容] 索引標籤。底下**安裝來源**，選擇**磁碟**選項按鈕。 選擇 **...** 按鈕並瀏覽至包含 Contoso 內容 （複製到上述的步驟中的本機資料夾） 的本機資料夾。 選擇 [HelpContentSetup.msha]。 Contoso 應現在會顯示為活頁簿中的活頁簿選取項目中。 選擇**新增**，然後選擇**更新**按鈕 （下圖右下角）。

19. 在 Contoso IDE 中，選擇 F1 鍵，以測試 F1 功能。

### <a name="additional-resources"></a>其他資源

針對執行階段 API，請參閱[Windows 說明 API](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx)。

如需有關如何運用說明 API 的詳細資訊，請參閱[說明檢視器程式碼範例](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)。

重大問題的更新，請參閱[說明檢視器讀我檔案](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)。