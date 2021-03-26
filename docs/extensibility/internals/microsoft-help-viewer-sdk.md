---
title: Microsoft Help Viewer SDK |Microsoft Docs
description: 瞭解 Visual Studio 說明檢視器工作，例如建立文章、建立說明檢視器內容商標套件，以及部署一組文章。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c53191c5f6e02c0b37d29f89a65119f1edab92ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063314"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

本文包含 Visual Studio 說明檢視器整合程式的下列工作：

-  (F1 支援建立主題) 

- 建立說明檢視器內容-商標套件

- 部署一組文章

- 將說明新增至 Visual Studio shell (整合或隔離) 

- 其他資源

## <a name="create-a-topic-f1-support"></a> (F1 支援建立主題) 

本節概述所呈現主題的元件、主題需求、如何建立主題的簡短描述 (包含 F1 支援需求) 最後是範例主題及其轉譯結果。

**說明檢視器主題總覽**

當針對轉譯呼叫某個主題時，說明檢視器會在安裝或上次更新時取得與主題相關聯的商標套件元素，以及 XHTML 的主題，並結合這兩個專案，以產生顯示內容視圖 (商標資料 + 主題資料) 。  商標套件包含標誌、內容行為的支援，以及商標文字 (著作權等 ) 。  如需商標套件元素的詳細資訊，請參閱下面的「建立商標套件」。  如果主題中沒有相關聯的商標套件，說明檢視器將會使用位於說明檢視器應用程式根目錄 (Branding_en-US. .mshc) 中的 [fallback 商標] 套件。

**說明檢視器主題需求**

若要在說明檢視器中正確轉譯，原始主題內容必須是 W3C Basic 1.1 XHTML。

主題通常包含兩個區段：

- 中繼資料 (請參閱內容中繼資料參考) ：主題的相關資料，例如主題的唯一識別碼、關鍵字值、主題目錄識別碼、父節點識別碼等。

- 本文內容：符合 W3C Basic 1.1 XHTML 的規範，包括支援的內容行為 (可折迭區域、程式碼片段等等。以下) 顯示完整清單。

Visual Studio 品牌套件支援的控制項：

- 連結

- CodeSnippet

- CollapsibleArea

- 繼承的成員

- LanguageSpecificText

支援的語言字串 (不區分大小寫) ：

- javascript

- csharp 或 c#

- >cplusplus 或 visualc + + 或 c + +

- jscript

- ... 或 vb

- f # 或 fsharp.core 或 fs

- 其他-表示語言名稱的字串

**建立說明檢視器主題**

建立名為 ContosoTopic4.htm 的新 XHTML 檔案，並在) 底下包含標題標記 (。

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

接下來，加入資料來定義主題 (自我品牌化或不) 、如何參考此主題的 F1、目錄中有此主題、其識別碼 (其他主題的連結參考) 等等。如需支援的中繼資料完整清單，請參閱下表的「內容中繼資料」表格。

- 在此情況下，我們將使用自己的商標套件，這是 Visual Studio 說明檢視器商標套件的變異。

- 將 F1 中繼名稱和值 ( "Microsoft. F1" content = "ContosoTopic4" ) ，以符合 IDE 屬性包中提供的 F1 值。  (如需詳細資訊，請參閱 F1 支援一節。 ) 這是在 IDE 中選擇 F1 時，與 IDE 內的 F1 呼叫相符的值，以顯示本主題。

- 新增主題識別碼。 這是其他主題用來連結至本主題的字串。 這是本主題的說明檢視器識別碼。

- 若為目錄，請新增此主題的父節點，以定義此主題 TOC 節點的出現位置。

- 若為目錄，請新增此主題的節點順序。 當父節點有 `n` 子節點數目時，請依照子節點的位置定義順序。 例如，本主題為4個子主題的第4個。

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

本文 (不包括主題的頁首和頁尾) 包含頁面連結、附注區段、可折迭區域、程式碼片段，以及特定語言文字的區段。  請參閱商標一節，以取得所顯示主題中這些區域的相關資訊。

1. 新增主題標題標記：  `<div class="title">Contoso Topic 4</div>`

2. 新增附注區段： `<div class="alert"> add your table tag and text </div>`

3. 新增可折迭區域：  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. 新增程式碼片段：  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. 新增程式碼語言特定文字：  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` 請注意，可 `devLangnu=` 讓您輸入其他語言。 例如， `devLangnu="Fortran"` 當代碼段 DisplayLanguage = fortran 時，會顯示 fortran

6. 新增頁面連結： `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> 注意：針對不支援的新「顯示語言」 (範例中，程式碼片段中的 F #、Cobol、Fortran) 程式碼顏色標示將會是單色。

**範例說明檢視器主題** 此程式碼說明如何定義中繼資料、程式碼片段、可折迭區域，以及特定語言的文字。

```html
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
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
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
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**F1 支援**

在 Visual Studio 中，選取 F1 會產生從 IDE 中的資料指標位置所提供的值，並根據游標位置，以提供的值 (填入「屬性包」。 當游標在功能 x 上時，功能 x 是使用中/焦點，並以值填入屬性包。  當選取 F1 時，會填入屬性包，Visual Studio F1 程式碼會查看客戶預設的說明來源是否為本機或線上 (online 是預設的) ，然後根據使用者的設定，建立適當的字串 (線上是預設) -shell execute (如需本機說明的預設值，請參閱「exe 啟動參數」的說明系統管理員指南，以及在參數清單中使用關鍵字的 MSDN URL。 () 

如果 F1 傳回三個字串（稱為多重值字串），請採用第一個詞彙，尋找點擊次數，如果找到，我們就完成了;如果沒有，請移至下一個字串。  順序很重要。 多值關鍵字的呈現方式應該是最長字串到最短的字串。  若要在多重值關鍵字的情況下確認這一點，請查看線上 F1 URL 字串，其中將包含所選的關鍵字。

在 Visual Studio 2012 中，我們刻意在線上和離線之間進行更強的劃分，如此一來，如果使用者的設定是線上的，則只會直接將 F1 要求傳遞至 MSDN 上的線上查詢服務，而不是透過我們在 Visual Studio 2010 中的 Help Library 代理程式路由傳送。 接著，我們會依賴「安裝的廠商內容 = true」狀態，判斷是否要在該內容中進行不同的動作。 若為 true，則會根據您想要為客戶支援的內容來執行此剖析和路由邏輯。 若為 false，則只需前往 MSDN。 如果使用者的設定為 [本機]，則所有呼叫都會移至本機說明引擎。

F1 流程圖：

![F1 流程](../../extensibility/internals/media/f1flow.png "F1flow")

當說明檢視器預設說明內容來源設定為線上時 (在瀏覽器中啟動) ：

- Visual Studio Partner (.VSP) 功能會對 F1 屬性包發出值， (屬性包的首碼。在登錄中找到之首碼的關鍵字和線上 URL) ： F1 將 .VSP URL + 參數傳送至瀏覽器。

- Visual Studio 功能 (語言編輯器、Visual Studio 特定功能表項目等 ) ： F1 將 Visual Studio URL 傳送至瀏覽器。

當說明檢視器預設說明內容來源設定為本機說明時 (在說明檢視器中啟動) ：

- 介於 F1 屬性包和本機存放區索引之間的關鍵字相符 (也就是屬性包前置詞。關鍵字 = 在本機存放區索引中找到的值) ： F1 會轉譯說明檢視器中的主題。

- Visual Studio 功能 (沒有任何選項可讓 .VSP 覆寫從 Visual Studio 功能發出的屬性包) ： F1 會在說明檢視器中呈現 Visual Studio 主題。

設定下列登錄值，以啟用供應商說明內容的 F1 回復。 F1 回溯表示說明檢視器設定為在線上尋找 F1 說明內容，並將廠商內容安裝在本機使用者的硬碟上。 雖然 [說明檢視器] 應該會查看內容的本機說明，不過預設設定是 [線上說明]。

1. 在 Help 2.3 登錄機碼底下設定 **VendorContent** 值：

   - 若為32位作業系統：

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = dword：00000001

   - 若為64位作業系統：

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = dword：00000001

2. 在 Help 2.3 登錄機碼下註冊夥伴命名空間：

   - 若為32位作業系統：

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<em> \\<命名 \> 空間</em>

      「位置」 = 「離線」

   - 若為64位作業系統：

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<em> \\<命名 \> 空間</em>

      「位置」 = 「離線」

**基底原生命名空間剖析**

若要開啟基底原生命名空間剖析，請在登錄中依名稱加入新的 DWORD： BaseNativeNamespaces，並將其值設定為 1 (其想要支援) 的目錄索引鍵下。  例如，如果您想要使用 Visual Studio 目錄，可以將機碼加入至路徑：

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

當遇到格式標頭/方法中的 F1 關鍵字時，會剖析 '/' 字元，以產生下列結構：

- HEADER：將會是可以用來在登錄中註冊的命名空間

- 方法：這會變成傳遞的關鍵字。

例如，假設有一個稱為 CustomLibrary 的自訂程式庫和一個稱為 MyTestMethod 的方法，則當 F1 要求出現時，就會格式化為 `CustomLibrary/MyTestMethod` 。

然後，使用者可以將 CustomLibrary 註冊為夥伴 hive 下的命名空間，並提供他們想要的任何位置金鑰，而且傳遞給查詢的關鍵字會是 MyTestMethod。

**在 IDE 中啟用 Help 調試工具**

新增下列登錄機碼和值：

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

值：顯示零售資料中的調試輸出：是

在 IDE 的 [說明] 功能表項目底下，選取 [ **Debug Help CoNtext**]。

**內容中繼資料**

在下表中，在括弧之間出現的任何字串都是必須以可辨識值取代的預留位置。 例如，在中 \<meta name="Microsoft.Help.Locale" content="[language code]" /> ，必須將 "[language code]" 取代為 "en-us" 之類的值。

|  (HTML 標記法的屬性)  | Description |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | 設定本主題的地區設定。 如果主題中使用此標籤，則只能使用一次，而且必須插入任何其他 Microsoft 說明標記的上方。 如果未使用此標籤，則會使用與產品地區設定相關聯的斷詞工具（如果有指定的話）來編制主題的主體文字。否則，會使用 en-us 斷詞工具。 此標記符合 ISOC RFC 4646。 為確保 Microsoft 說明正常運作，請使用這個屬性，而不是一般語言屬性。 |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | 如果也使用其他地區設定，則設定本主題的地區設定。 如果在主題中使用此標籤，則只能使用一次。 當目錄包含多種語言的內容時，請使用此標記。 目錄中的多個主題可以有相同的識別碼，但每個主題都必須指定唯一的 TopicLocale。 指定符合目錄地區設定之 TopicLocale 的主題，是顯示在目錄中的主題。 不過，主題的所有語言版本都會顯示在搜尋結果中。 |
| \< title>職務\</title> | 指定本主題的標題。 此標記是必要的，而且必須只在主題中使用一次。 如果主題主體未包含標題 \<div> 區段，此標題會顯示在主題和目錄中。 |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | 指定顯示在 [說明檢視器] 之 [索引] 窗格中的連結文字。 按一下連結時，就會顯示主題。 您可以為主題指定多個索引關鍵字，或者，如果您不想要讓此主題的連結出現在索引中，可以省略這個標記。 舊版說明的 "K" 關鍵字可以轉換成這個屬性。 |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | 設定本主題的識別碼。 此標記是必要的，而且必須只在主題中使用一次。 識別碼在具有相同地區設定的目錄中的主題之間必須是唯一的。 在另一個主題中，您可以使用此識別碼來建立此主題的連結。 |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | 指定本主題的 F1 關鍵字。 您可以針對主題指定多個 F1 關鍵字，或者，如果您不想在應用程式使用者按下 F1 時顯示此主題，也可以省略這個標記。 通常只會針對主題指定一個 F1 關鍵字。 舊版說明的 "F" 關鍵字可以轉換成這個屬性。 |
| \< meta name="Description" content="[topic description]" /> | 提供本主題內容的簡短摘要。 如果在主題中使用此標籤，則只能使用一次。 這個屬性是由查詢程式庫直接存取;它不會儲存在索引檔中。 |
| meta name = "TocParent" content = "[parent_Id]"/> | 在目錄中指定本主題的父主題。 此標記是必要的，而且必須只在主題中使用一次。 值是父系的 Microsoft.Help.Id。 主題在目錄中只能有一個位置。 "-1" 被視為 TOC 根目錄的主題識別碼。 在中 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ，該頁面是說明檢視器首頁。 這是我們特別將 TocParent =-1 新增至某些主題，以確保它們會顯示在最上層的原因。 說明檢視器首頁是系統頁面，因此不可取代。 如果 .VSP 嘗試新增識別碼為-1 的頁面，它可能會新增至內容集，但說明檢視器一律會使用系統頁面-說明檢視器首頁 |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | 指定本主題在目錄中的相對於其對等主題的顯示位置。 此標記是必要的，而且必須只在主題中使用一次。 值為整數。 指定較低值整數的主題會出現在指定較高值整數的主題上方。 |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | 指定本主題所描述的產品。 如果在主題中使用此標籤，則只能使用一次。 這項資訊也可以做為傳遞給說明索引子的參數提供。 |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | 指定本主題所描述的產品版本。 如果在主題中使用此標籤，則只能使用一次。 這項資訊也可以做為傳遞給說明索引子的參數提供。 |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | 由產品用來識別內容的小節。 您可以識別主題的多個子區段，或者，如果您不想要連結來識別任何子區段，也可以省略此標記。 當主題從較早版本的說明轉換時，此標記可用來儲存 TargetOS 和 TargetFrameworkMoniker 的屬性。 內容的格式為 AttributeName： AttributeValue。 |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | 當目錄中有多個版本時，指定此主題版本。 因為 Microsoft.Help.Id 不保證是唯一的，所以當目錄中有多個版本的主題時，就需要這個標記，例如，當目錄包含 .NET Framework 3.5 的主題和 .NET Framework 4 的主題，而且兩者都有相同的 Microsoft.Help.Id 時。 |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | 指定本主題是否使用 Help Library 管理員啟動商標套件，或主題專屬的商標套件。 這個標記必須是 TRUE 或 FALSE。 若為 TRUE，則相關主題的商標套件會覆寫 [Help Library 管理員] 開始時所設定的商標套件，讓主題如預期轉譯，即使與其他內容的轉譯不同也一樣。 如果為 FALSE，則會根據 [Help Library 管理員] 開始時所設定的商標套件，轉譯目前的主題。 根據預設，除非 SelfBranded 變數宣告為 TRUE，否則 Help Library 管理員會假設自我商標為 false：因此，您不需要宣告 \<meta name="SelfBranded" content="FALSE"/> 。 |

## <a name="create-a-branding-package"></a>建立商標套件

Visual Studio 版本包含許多不同的 Visual Studio 產品，包括 Visual Studio 合作夥伴的隔離和整合式 shell。  每一項產品都需要某種程度的主題型說明內容支援，對產品而言是唯一的。  例如，Visual Studio 主題需要有一致的品牌簡報，而 SQL Studio （可包裝 ISO Shell）則需要各自獨特的「說明」內容商標給每個主題。  整合式 Shell 夥伴可能會想要其說明主題位於父系 Visual Studio 產品說明內容中，同時保有自己的主題品牌。

商標套件是由包含說明檢視器的產品所安裝。  針對 Visual Studio 產品：

-  () Branding_ 的「退回品牌」套件 \<locale> 會安裝在說明檢視器2.3 應用程式根目錄 (範例： C:\Program Files (x86) \Microsoft help Viewer\v2.3) 由說明檢視器語言套件提供。  這適用于未安裝產品品牌套件 (未安裝任何內容) 或安裝的商標套件已損毀的情況。  使用應用程式的根後備商標套件時，會忽略 Visual Studio 元素 (標誌和意見反應) 。

- 從內容套件服務安裝 Visual Studio 內容時，也會在) 的第一次內容安裝案例 (安裝商標套件。  如果已更新商標套件，則會在下一次內容更新或其他套件安裝動作發生時安裝更新。

Microsoft Help Viewer 根據主題中繼資料支援主題的商標。

- 其中主題元資料定義了自我品牌 = true，將主題依原樣轉譯，請勿在品牌)  (執行任何動作。

- 其中主題元資料定義了自我品牌 = false，請使用與 TopicVendor 中繼資料值相關聯的商標套件。

- 其中主題元資料定義 name = "TopicVendor" content = \< branding package name in vendor MSHA> ，請使用內容值中定義的商標套件。

- 在 Visual Studio 目錄內，有商標套件的優先順序應用。  首先會套用 Visual Studio 預設商標，然後，如果在主題中繼資料中定義，並且支援與相關聯的品牌套件 (（如安裝 .msha) 中所定義），則會將廠商定義的商標套用為覆寫。

商標元素通常會分成三個主要類別：

- 標頭元素 (範例包括意見反應連結、條件免責聲明文字、標誌) 

- 內容行為 (範例包括展開/折迭控制項文字元素和程式碼片段元素) 

- 頁尾元素 (範例著作權) 

視為品牌要素的專案包含此規格) 中詳述的 (：

- 目錄/產品標誌 (範例、Visual Studio) 

- 意見反應連結和電子郵件元素

- 免責聲明文字

- 著作權文字

Visual Studio Help Viewer 商標套件中的支援檔案包括：

- 圖形 (標誌、圖示等 ) 

- Branding.js-支援內容行為的指令檔

- 在目錄內容中一致使用的 Branding.xml 字串。  注意：若要在 branding.xml 中 Visual Studio 當地語系化文字元素，請包含 _locID = " \<unique value> "

- 商標 .css 樣式定義的簡報一致性

- 列印：一致列印簡報的 css 樣式定義

如先前所述，商標套件與主題相關聯：

- 在中繼資料中定義 SelfBranded = false 時，主題會繼承類別目錄商標套件

- 或當 SelfBranded = false，且在 .MSHA 中定義了唯一的商標套件，且在內容安裝時可供使用

針對執行自訂商標套件的 .Vsps (.VSP 內容，SelfBranded = True) ，要繼續的其中一種方式就是從 [說明檢視器] (安裝的 [取代品牌) ] 套件開始，然後視需要變更檔案的名稱。  .Mshc 檔案 \<locale> 是副檔名變更為 .mshc 的 zip 檔案，因此只要將副檔名從 .mshc 變更為 .zip，並將內容解壓縮。 Branding_  請參閱下方的商標套件元素，並視需要進行修改 (例如，將標誌變更為 .VSP 標誌，以及 Branding.xml 檔案中標誌的參考、依 .VSP 詳細資訊更新 Branding.xml 等 ) 。

當所有修改都完成時，請建立包含所需商標元素的 zip 檔案，並將副檔名變更為 .mshc。

若要建立自訂商標套件的關聯，請建立 .MSHA，其中包含品牌 .mshc 檔案的參考，以及包含) 主題的 content .mshc (。  請參閱下面的「.MSHA」，以瞭解如何建立基本 .MSHA。

Branding.xml 檔案包含的專案清單，會在主題包含時，用來在主題中以一致的方式呈現特定專案 \<meta name="Microsoft.Help.SelfBranded" content="false"/> 。  以下列出 Branding.xml 檔案中的 Visual Studio 元素清單。  這份清單的目的是作為 ISO Shell 採用者的範本，在其中修改這些元素 (例如標誌、意見反應和著作權) ，以符合自己的產品商標需求。

注意： "{n}" 記下的變數具有程式碼相依性-移除或變更這些值將會導致錯誤，而且可能會導致應用程式損毀。 當地語系化識別碼 (範例 _locID = "codesnippet. n" ) 包含在 Visual Studio 商標套件中。

**Branding.xml**

| 元素 | 描述 |
| - | - |
| 功能： | **CollapsibleArea** |
| 使用︰ | 展開折迭內容控制項文字 |
| **Element** | **值** |
| ExpandText | 展開 |
| CollapseText | 摺疊 |
| 功能： | **CodeSnippet** |
| 使用︰ | 程式碼片段控制項文字。  注意：具有「非中斷」空間的程式碼片段內容將會變更為「空格」。 |
| **Element** | **值** |
| CopyToClipboard | 複製至剪貼簿 |
| ViewColorizedText | View 以色彩標示 |
| CombinedVBTabDisplayLanguage | Visual Basic (範例)  |
| VBDeclaration | 宣告 |
| VBUsage | 使用方式 |
| 功能： | **意見反應、頁尾和標誌** |
| 使用︰ | 提供意見反應控制項，讓客戶透過電子郵件提供目前主題的意見反應。  內容的著作權文字。  標誌定義。 |
| **Element** | **值 (可以修改這些字串，以符合採用者需求。 )** |
| 版權 | © 2013 Microsoft Corporation。 著作權所有，並保留一切權利。 |
| SendFeedback | \<a href="{0}" {1}>將 \</a> 本主題的意見反應傳送給 Microsoft。 |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| 功能： | **免責 聲明** |
| 使用︰ | 機器翻譯內容的一組案例特定免責聲明。 |
| **Element** | **值** |
| MT_Editable | 本文已轉譯機器翻譯。 如果您有網際網路連線，請選取 [線上查看此主題]，以同時使用原始英文內容來查看此頁面的可編輯模式。 |
| MT_NonEditable | 本文已轉譯機器翻譯。 如果您有網際網路連線，請選取 [線上查看此主題]，以同時使用原始英文內容來查看此頁面的可編輯模式。 |
| MT_QualityEditable | 本文是以手動方式轉譯。 如果您有網際網路連線，請選取 [線上查看此主題]，以同時使用原始英文內容來查看此頁面的可編輯模式。 |
| MT_QualityNonEditable | 本文是以手動方式轉譯。 如果您有網際網路連線，請選取 [線上查看此主題]，以同時使用原始英文內容來查看此頁面的可編輯模式。 |
| MT_BetaContents | 本文是針對初稿版本轉譯的機器翻譯。 如果您有網際網路連線，請選取 [線上查看此主題]，以同時使用原始英文內容來查看此頁面的可編輯模式。 |
| MT_BetaRecycledContents | 本文是以手動方式轉譯，以進行初步發行。 如果您有網際網路連線，請選取 [線上查看此主題]，以同時使用原始英文內容來查看此頁面的可編輯模式。 |
| 功能： | **LinkTable** |
| 使用︰ | 線上主題連結的支援 |
| **Element** | **值** |
| LinkTableTitle | 連結資料表 |
| TopicEnuLinkText | 請參閱本主題的英文版 \</a> ，此主題可在您的電腦上取得。 |
| TopicOnlineLinkText | 線上觀看本主題 \<a href="{0}" {1}>\</a> |
| OnlineText | 線上 |
| 功能： | **影片音訊控制項** |
| 使用︰ | 顯示影片內容的元素和文字 |
| **Element** | **值** |
| MultiMediaNotSupported | 必須安裝 Internet Explorer 9 或更新版本，才能支援 {0} 內容。 |
| VideoText | 顯示影片 |
| AudioText | 串流音訊 |
| OnlineVideoLinkText | \<p>若要查看與此主題相關的影片，請按一下 {0} \<a href="{1}"> {2} 這裡 \</a> 。\</p> |
| OnlineAudioLinkText | \<p>若要聆聽與此主題相關聯的音訊，請按一下 {0} \<a href="{1}"> {2} 這裡 \</a> 。\</p> |
| 功能： | **未安裝內容的控制項** |
| 使用︰ |  (字串的文字元素) 用於轉譯 contentnotinstalled.htm |
| **Element** | **值** |
| ContentNotInstalledTitle | 在您的電腦上找不到任何內容。 |
| ContentNotInstalledDownloadContentText | \<p>若要將內容下載到您的電腦，請 \<a href="{0}" {1}> 按一下 [管理] 索引標籤 \</a> 。\</p> |
| ContentNotInstalledText | \<p>您的電腦上未安裝任何內容。 請參閱您的系統管理員以取得本機說明內容安裝。\</p> |
| 功能： | **找不到主題控制項** |
| 使用︰ |  (字串的文字元素) 用於轉譯 topicnotfound.htm |
| **Element** | **值** |
| TopicNotFoundTitle | 在您的電腦上找不到要求的主題。 |
| TopicNotFoundViewOnlineText | \<p>在您的電腦上找不到您所要求的主題，但是您可以在 \<a href="{0}" {1}> 線上觀看該主題 \</a> 。\</p> |
| TopicNotFoundDownloadContentText | \<p>請參閱流覽窗格以取得類似主題的連結，或 \<a href="{0}" {1}> 按一下 [管理] 索引標籤， \</a> 將內容下載到您的電腦。\</p> |
| TopicNotFoundText | \<p>在您的電腦上找不到您所要求的主題。\</p> |
| 功能： | **主題損毀控制項** |
| 使用︰ |  (字串的文字元素) 用於轉譯 topiccorrupted.htm |
| **Element** | **值** |
| TopicCorruptedTitle | 無法顯示要求的主題。 |
| TopicCorruptedViewOnlineText | \<p>說明檢視器無法顯示要求的主題。 主題的內容或基礎系統相依性中可能有錯誤。\</p> |
| 功能： | **首頁控制項** |
| 使用︰ | 支援說明檢視器最上層節點內容顯示的文字。 |
| **Element** | **值** |
| HomePageTitle | 說明檢視器首頁 |
| HomePageIntroduction | \<p>歡迎使用 Microsoft Help Viewer，這是使用 Microsoft 工具、產品、技術和服務之每個人的基本資訊來源。 說明檢視器可讓您存取使用説明和參考資訊、範例程式碼、技術文章等等。 若要尋找您需要的內容，請流覽目錄、使用全文檢索搜尋，或使用關鍵字索引流覽內容。\</p> |
| HomePageContentInstallText | \<p>\<br />使用 [ \<a href="{0}" {1}> 管理內容] 索引標籤 \</a> 來執行下列動作： \<ul> \<li> 將內容新增至您的電腦。 \</li> \<li>檢查您的本機內容是否有更新。 \</li> \<li>從您的電腦移除內容。\</li>\</ul>\</p> |
| HomePageInstalledBooks | 已安裝的書籍 |
| HomePageNoBooksInstalled | 在您的電腦上找不到任何內容。 |
| HomePageHelpSettings | 說明內容設定 |
| HomePageHelpSettingsText | \<p>您目前的設定是本機說明。 說明檢視器會顯示您已在電腦上安裝的內容。 \<br />若要變更說明內容的來源，請在 [Visual Studio] 功能表列上，選擇 [說明] \<span style="{0}"> 、[設定說明喜好設定] \</span> 。\<br />\</p> |
| 兆 位元組 | MB |

**branding.js**

branding.js 檔案包含 Visual Studio 說明檢視器商標元素所使用的 JavaScript。  以下是商標元素和支援的 JavaScript 函式清單。  要針對此檔案當地語系化的所有字串都會定義在此檔案頂端的「可當地語系化的字串」區段中。  已針對 branding.js 檔案內的 loc 字串建立 ICL 檔案。

|**商標功能**|**JavaScript 函數**|**說明**|
|-|-|-|
|無 功。。。||定義變數|
|取得使用者程式碼語言|setUserPreferenceLang|將索引編號對應至程式碼語言|
|設定並取得 cookie 值|System.windows.application.getcookie、System.windows.application.setcookie||
|繼承的成員|changeMembersLabel|展開/折迭繼承的成員|
|當 SelfBranded = False 時|onLoad|讀取查詢字串以檢查它是否為列印要求。  設定所有 codesnippets 以將焦點放在 [使用者慣用] 索引標籤。 如果是列印要求，請將 isPrinterFriendly 設為 true。 檢查高對比模式。|
|程式碼片段|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|將所有可折迭的控制項物件寫入清單中。|
||CA_Click|根據可折迭區域的狀態，定義要顯示的影像和文字|
|標誌的對比支援|isBlackBackground () |呼叫以判斷背景是否為黑色。  只有在高對比模式下才會正確。|
||isHighContrast () |使用彩色的範圍來偵測高對比模式|
||onHighContrast (黑色) |偵測到高對比時呼叫|
|.LST 功能|||
||addToLanSpecTextIdSet (識別碼) ||
||updateLST (currentLang) ||
||getDevLangFromCodeSnippet (lang) ||
|多媒體功能|標題 (開始、結束、文字、樣式) ||
||findAllMediaControls (normalizedId) ||
||getActivePlayer (normalizedId) ||
||captionsOnOff (識別碼) ||
||toSeconds (t) ||
||getAllComments (節點) ||
||styleRectify (styleName、Stylevalue]) ||
||showCC (識別碼) ||
||標題 (識別碼) ||

**HTM 檔案**

商標套件包含一組 HTM 檔案，這些檔案可支援傳達重要資訊以協助內容使用者的案例，例如，包含描述已安裝之內容集的首頁，以及在本機主題集合中找不到主題時，會告知使用者的網頁。 每項產品都可以修改這些 HTM 檔案。  ISO Shell 廠商能夠採用預設商標套件，並變更這些頁面的行為和內容，以符合其需求。  這些檔案會參考其各自的商標套件，以便品牌標記從 branding.xml 檔案取得對應的內容。

|**檔案**|**使用**|**顯示的內容來源**|
|-|-|-|
|homepage.htm|此頁面會顯示目前已安裝的內容，以及任何其他適合向使用者呈現其內容的訊息。  這個檔案有額外的中繼資料屬性 "Microsoft.Help.Id" content = "-1"，它會將此內容放在本機內容目錄的頂端。||
||<META_HOME_PAGE_TITLE_ADD/>|Branding.xml，標記 \<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Branding.xml，標記 \<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|Branding.xml，標記 \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|標題區段 Branding.xml 標記 \<HomePageInstalledBooks> ，  \<HomePageNoBooksInstalled> 也就是在未安裝任何書籍時，從應用程式產生的資料。|
||<HOME_PAGE_SETTINGS_SECTION_ADD/>|標題區段 Branding.xml 標記 \<HomePageHelpSettings> 、區段文字 \<HomePageHelpSettingsText> 。|
|topiccorrupted.htm|當主題存在於本機群組中，但因為某些原因而無法顯示 (損毀的內容) 。||
||<META_TOPIC_CORRUPTED_TITLE_ADD/>|Branding.xml，標記 \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD/>|Branding.xml，標記 \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|在本機內容集中找不到主題，也無法在線上使用||
||<META_TOPIC_NOT_FOUND_TITLE_ADD/>|Branding.xml，標記 \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD/>|Branding.xml，標記 \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD/>|Branding.xml，標記 \<TopicNotFoundText>|
|contentnotinstalled.htm|如果未針對產品安裝任何本機內容，則為。||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Branding.xml，標記 \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD/>|Branding.xml，標記 \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD/>|Branding.xml，標記 \<ContentNotInstalledText>|

**CSS 檔案**

Visual Studio 說明檢視器商標套件包含兩個 css 檔案，以支援一致的 Visual Studio 說明內容展示：

- 商標 .css-包含用來轉譯的 css 元素，其中 SelfBranded = false

- .Css-包含用來轉譯的 css 元素，其中 SelfBranded = false

商標 .css 檔案包含 Visual Studio 主題呈現的定義 (警告是套件服務 Branding_ 的 .mshc 中包含的商標 \<locale> 可能會變更) 。

**圖形檔案**

Visual Studio 內容會顯示 Visual Studio 標誌以及其他圖形。  Visual Studio 說明檢視器商標套件中的完整圖形檔案清單如下所示。

|**檔案**|**使用**|**範例**|
|-|-|-|
|clear.gif|用來呈現可折迭區域||
|footer_slice.gif|頁尾簡報||
|info_icon.gif|顯示資訊時使用|免責聲明|
|online_icon.gif|此圖示會與線上連結相關聯||
|tabLeftBD.gif|用來呈現程式碼片段容器||
|tabRightBD.gif|用來呈現程式碼片段容器||
|vs_logo_bk.gif|用於 Branding.xml 標記中所定義的一般對比標誌參考 \<LogoFileName> 。  針對 Visual Studio 產品，標誌名稱是 vs_logo_bk.gif。||
|vs_logo_wh.gif|用於 Branding.xml 標記中所定義的一般高標誌參考 \<LogoFileNameHC> 。  針對 Visual Studio 產品，標誌名稱是 vs_logo_wh.gif。||
|ccOff.png|字幕圖形||
|ccOn.png|字幕圖形||
|ImageSprite.png|用來呈現可折迭區域|展開或折迭圖形|

## <a name="deploy-a-set-of-topics"></a>部署一組主題

這是簡單且快速的教學課程，可讓您建立包含 .MSHA 檔案的說明檢視器內容部署集，以及包含主題的一組 cab 或 MSHCs。 .MSHA 是一種 XML 檔案，可描述一組 cab 或 .MSHC 檔案。 說明檢視器可以讀取 .MSHA，以取得 (的內容清單。CAB 或。.MSHC 檔) 可用於本機安裝。

這只是描述說明檢視器 .MSHA 之非常基本 XML 架構的入門。  此簡短總覽和範例 Helpcontentsetup.msha .msha 的範例如下。

.MSHA 的名稱（基於此入門的目的）是 Helpcontentsetup.msha. .msha (檔案的名稱可以是任何副檔名為的檔案。.MSHA) 。 Helpcontentsetup.msha. .msha (範例) 應包含可用的 cab 或 MSHCs 清單。  檔案類型在 .MSHA 中必須是一致的 (不支援 .MSHA 和 CAB 檔案類型的組合) 。 針對每個 CAB 或 .mshc，應該會有一個 \<div class="package"> ... \</div> (請參閱下面的範例) 。

注意：在下列的實範例中，我們已加入商標套件。 為了取得所需的 Visual Studio 內容轉譯元素和內容行為，這是不可或缺的。

範例 Helpcontentsetup.msha. .msha 檔案： (以您的檔案名取代「內容集名稱1」和「內容集名稱2」等等。 ) 

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
</div>.
```

1. 建立本機資料夾，類似 "C:\SampleContent"

2. 在此範例中，我們將使用 .MSHC 檔案來包含主題。  .MSHC 是副檔名從 .zip 變更為的 zip。.MSHC.

3. 將下列 Helpcontentsetup.msha 建立為文字檔， (記事本用來建立) 的檔案，並將其儲存至上述的已注明資料夾 (請參閱步驟 1) 。

類別 "商標" 存在，而且是唯一的。 商標 .mshc 包含在此入門中，因此安裝的內容將會具有商標，而且 MSHCs 中包含的內容行為將具有商標套件中包含的適當支援元素。 如果沒有這種情況，當系統尋找的支援專案不屬於已安裝) 內容的已翻錄 (時，將會產生錯誤。

若要取得 Visual Studio 商標套件，請將 C:\Program 檔案中的 Branding_en-.mshc 檔案複製 (x86) \Microsoft Help Viewer\v2.3\ 至您的工作資料夾。

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

**總結**

使用和擴充上述步驟，可讓 .Vsps 部署 Visual Studio 說明檢視器的內容集。

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>將說明新增至 Visual Studio Shell (整合式和隔離) 

**簡介**

本逐步解說示範如何將說明內容併入 Visual Studio Shell 應用程式，然後加以部署。

**需求**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 獨立模式 Shell 可轉散發套件](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**概觀**

[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Shell 是 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 您可以用來作為應用程式基礎的 IDE 版本。 這類應用程式包含隔離的 Shell 以及您所建立的擴充功能。 使用 SDK 中包含的獨立 Shell 專案範本 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 來建立擴充功能。

建立隔離式 Shell 型應用程式及其說明的基本步驟：

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] (Microsoft 下載中心) 取得 ISO Shell 可轉散發套件。

2. 在 Visual Studio 中，建立以隔離式 Shell 為基礎的說明延伸模組，例如本逐步解說稍後所述的 Contoso 說明延伸模組。

3. 將延伸模組和 ISO Shell 可轉散發套件包裝到部署 MSI (應用程式安裝) 。 本逐步解說不包含設定步驟。

建立 Visual Studio 內容存放區。 針對整合式 Shell 案例，請將 Visual Studio12 變更為產品目錄名稱，如下所示：

- 建立資料夾 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15。

- 建立名為 CatalogType.xml 的檔案，並將它新增至資料夾。 檔案應該包含下列程式程式碼：

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

在登錄中定義內容存放區。 針對整合式 Shell，將 VisualStudio15 變更為產品目錄名稱：

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   索引鍵： LocationPath 字串值： C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   索引鍵： CatalogName 字串值： [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 檔

**建立專案**

若要建立隔離式 Shell 擴充功能：

1. 在 Visual Studio 的 [檔案] 下，選擇 [**新增專案**]，在 **[****其他專案類型** **] 下選擇**[擴充性]，然後選擇 [ **Visual Studio Shell 隔離**]。 將專案命名 `ContosoHelpShell` 為) ，以根據 Visual Studio 獨立模式 Shell 範本建立擴充性專案。

2. 在方案總管的 ContosoHelpShellUI 專案中，開啟 [資源檔] 資料夾中的 [System.windows.input.applicationcommands.paste. .vsct]。 請確定此行已標記為批註 (搜尋 "No_Help" ) ： `<!-- <define name="No_HelpMenuCommands"/> -->`

3. 選擇 F5 鍵來編譯和執行 **調試**。 在獨立 Shell IDE 的實驗實例中，選擇 [說明 **] 功能表。** 確定已顯示 [ **View** 說明]、[ **新增] 和 [移除說明內容**]，並顯示 [設定說明 **喜好設定** ] 命令。

4. 在方案總管的 ContosHelpShell 專案中，開啟 [Shell 自訂] 資料夾中的 ContosoHelpShell. .pkgdef。 若要定義 Contoso Help catalog，請新增下列幾行：

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. 在方案總管的 ContosHelpShell 專案中，開啟 [Shell 自訂] 資料夾中的 ContosoHelpShell .pkgdef。 若要啟用 F1 說明，請新增下列程式程式碼：

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

6. 在方案總管的 ContosoHelpShell 方案內容功能表上，選擇 [ **屬性** ] 功能表項目。 在 [設定 **屬性**] 下，選取 [ **設定管理員**]。 在 [設定] **資料行中** ，將每個 "Debug" 值變更為 "Release"。

7. 建置方案。 這會在發行資料夾中建立一組檔案，將在下一節中使用。

若要測試此測試是否已部署：

1. 在您要部署 Contoso 的電腦上，從上述) ISO Shell 安裝下載的 (。

2. 在 \Program 檔案中建立資料夾 \\ (x86) \\ ，並為其命名 `Contoso` 。

3. 將 ContosoHelpShell 版本資料夾中的內容複寫到 \\ \Program 檔案 (x86) \contoso\ 資料夾。

4. 選擇 [**開始**] 功能表中的 [**執行**]，然後輸入，啟動登錄編輯程式 `Regedit` 。 在 [登錄編輯程式] 中 **，選擇 [** 檔案]，然後匯 **入**。 流覽至 ContosoHelpShell 專案資料夾。 在 [ContosoHelpShell] 子資料夾中，選擇 [ContosoHelpShell]。

5. 建立內容存放區：

    針對 ISO Shell-建立 Contoso 內容存放區 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    若為 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 整合式 Shell，請建立資料夾 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15

6. 建立 CatalogType.xml，並新增至內容存放區 (上一個步驟) 包含：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. 新增下列登錄機碼：

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key： LocationPath 字串值：

    針對 ISO Shell：

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 整合式 Shell：

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    索引鍵： CatalogName 字串值： [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 檔。 針對 ISO Shell，這是您的目錄名稱。

8. 將您的內容 (cab 或 .MSHC 和 .MSHA) 複製到本機資料夾。

9. 用於測試內容存放區的整合式 Shell 命令列範例。 針對 ISO Shell，請視需要變更目錄和 launchingApp 值以符合產品。

     "C:\Program Files (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe"/catalogName VisualStudio15/helpQuery method = "page&id = ContosoTopic0"/launchingApp Microsoft，VisualStudio，12。0

10. 從 Contoso 應用程式根) 啟動 Contoso 應用程式 (。 在 [ISO Shell] 中，選擇 [說明 **] 功能表項目** ，然後將 [ **設定說明喜好設定** ] 變更為 [ **使用本機** 說明]。

11. 在 shell 中，選擇 [說明 **] 功能表項目** ，然後 **查看**[說明]。 本機說明檢視器應該會啟動。 選擇 [ **管理內容** ] 索引標籤。在 [ **安裝來源**] 下，選擇 [ **磁片** ] 選項按鈕。 選擇 [ **...** ] 按鈕，然後流覽至包含 Contoso 內容的本機資料夾， (複製到上述步驟中的本機資料夾) 。 選擇 [Helpcontentsetup.msha] .msha。 Contoso 現在應該會顯示為書籍選取專案中的書。 選擇 [ **新增**]，然後選擇 [ **更新** ] 按鈕 (右下角) 。

12. 在 Contoso IDE 中，選擇 F1 鍵以測試 F1 功能。

## <a name="additional-resources"></a>其他資源

如需執行時間 API 的詳細資訊，請參閱 [Windows 說明 api](/previous-versions/windows/desktop/helpapi/helpapi-portal)。

如需如何運用說明 API 的詳細資訊，請參閱說明 [檢視器程式碼範例](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)。

您可以在 [開發人員社群](https://aka.ms/feedback/suggest?space=8)提交功能建議。
