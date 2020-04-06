---
title: 微軟幫助查看器 SDK |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707146"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

本文包含可視化工作室説明查看器集成商的以下任務:

- 建立主題(F1 支援)

- 建立說明檢視器內容品牌套件

- 部署文章

- 向視覺化工作室外殼添加説明(整合或隔離)

- 其他資源

## <a name="create-a-topic-f1-support"></a>建立主題(F1 支援)

本節概述了呈現的主題的元件、主題要求、有關如何創建主題的簡短說明(包括 F1 支援要求),最後提供了一個示例主題及其呈現的結果。

**說明檢視器主題概述**

當調用主題進行呈現時,説明查看器獲取在安裝或上次更新時與主題關聯的品牌包元素以及主題 XHTML,並將兩者合併以產生呈現的內容視圖(品牌數據 + 主題數據)。  品牌包包含徽標、對內容行為的支援以及品牌文本(版權等)。  有關品牌包元素的詳細資訊,請參閱下面的"創建品牌包"。  如果沒有與主題關聯的品牌包,幫助查看器將使用位於説明查看器應用程式根(Branding_en-US.mshc)中的回退品牌包。

**說明檢視者主題要求**

要在説明查看器中正確呈現,原始主題內容必須是 W3C 基本 1.1 XHTML。

主題通常包含兩個部分:

- 元資料(請參閱內容元資料參考):有關主題的數據,例如主題唯一 ID、關鍵字值、主題 TOC ID、父節點 ID 等。

- 正文內容:符合 W3C 基本 1.1 XHTML,其中包括支援的內容行為(可摺疊區域、代碼段等)。完整清單如下所示)。

支援視覺化工作室品牌包的控制項:

- 連結

- 代碼段

- 可摺疊區域

- 繼承成員

- 語言特異性文字

支援的語言字串(不區分大小寫):

- javascript

- csharp 或 c#

- 加號或視覺+或 c#

- jscript

- 視覺基礎或 vb

- f# 或 fsharp 或 fs

- 其他 - 表示語言名稱的字串

**建立說明檢視器主題**

創建新的 XHTML 文檔名為 ContosoTopic4.htm,並包括標題標記(如下所示)。

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

接下來,添加數據以定義如何呈現主題(是否自品牌)、如何為 F1 引用此主題、該主題存在於 TOC 中、其 ID(供其他主題連結引用)等。有關支援的元資料的完整清單,請參閱下面的「內容元數據」表。

- 在這種情況下,我們將使用我們自己的品牌包,可視化工作室幫助查看器品牌包的變體。

- 添加與 IDE 屬性袋中提供的 F1 值匹配的 F1 元名稱和值("Microsoft.Help.F1"內容="ContosoTopic4")。 (有關詳細資訊,請參閱 F1 支援部分。這是從 IDE 中與 F1 調用匹配的值,用於在 IDE 中選擇 F1 時顯示此主題。

- 添加主題識別碼。 這是其他主題用於連結到本主題的字串。 它是本主題的幫助查看器 ID。

- 對於 TOC,添加本主題的父節點以定義本主題 TOC 節點的顯示位置。

- 對於 TOC,添加本主題的節點順序。 當父節點具有`n`子節點數時,請按子節點的順序定義本主題的位置。 例如,本主題是 4 個子主題中的數位 4。

中繼資料範例

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

**主題正文**

主題的正文(不包括標題和頁腳)將包含頁面連結、註釋部分、可摺疊區域、代碼段和特定於語言的文本部分。  有關所介紹主題的這些領域的資訊,請參閱品牌部分。

1. 新增主題標題標記:`<div class="title">Contoso Topic 4</div>`

2. 新增註解部份:`<div class="alert"> add your table tag and text </div>`

3. 新增可折疊區域:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. 新增代碼:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. 新增特定於代碼語言的文本:`<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />`允許您輸入`devLangnu=`其他 語言的註解。 例如,`devLangnu="Fortran"`在程式碼段顯示語言 + Fortran 時顯示 Fortran

6. 新增頁面連結:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> 注意:對於不支援的新"顯示語言"(例如,F#、Cobol、Fortran),代碼段中的代碼著色將是單色的。

**說明檢視器主題範例**該代碼說明瞭如何定義中繼資料、程式碼段、可摺疊區域和特定於語言的文本。

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

在 Visual Studio 中,選擇 F1 會生成從游標放置在 IDE 中提供的值,並填充帶有提供值的「屬性包」(基於游標位置)。 當游標超過特徵 x 時,要素 x 處於活動狀態/聚焦,並且用值填充屬性包。  選擇 F1 時,將填充屬性套件,Visual Studio F1 程式碼檢視客戶預設説明來源是本地還是聯機(聯機是預設值),然後根據使用者設定(聯機是預設值) 創建相應的字串 - shell 執行(請參閱説明管理員指南,瞭解 exe 啟動參數),以及屬性袋中的本地説明檢視器 + 關鍵字(如果本地説明是預設值)的參數或參數清單中包含關鍵字的 MSDN URL。

如果為 F1 返回三個字串(稱為多值字串),則採用第一個術語,查找命中,如果找到,我們就完成;如果沒有,則移動到下一個字串。  訂單很重要。 多值關鍵字的表示應為最長字串到最短字串。  要驗證多值關鍵字的情況,請查看連線 F1 URL 字串,該字串將包括所選關鍵字。

在 Visual Studio 2012 中,我們有意在連線和離線之間進行更強烈的劃分,因此,如果使用者的設置是連線的,則只需將 F1 請求直接傳遞到 MSDN 上的連線查詢服務,而不是透過 Visual Studio 2010 中的説明庫代理路由。 然後,我們依靠"已安裝的供應商內容 = true"的狀態來確定是否在這種情況下執行不同操作。 如果為 true,則根據您希望支援您的客戶的內容執行此分析和路由邏輯。 如果為 false,則只需轉到 MSDN。 如果用戶的設置是本地,則所有呼叫都轉到本地説明引擎。

F1 流程圖:

![F1 流程](../../extensibility/internals/media/f1flow.png "F1流")

使用說明檢視器預設幫助內容來源設定為線上(在瀏覽器中啟動):

- Visual Studio 合作夥伴 (VSP) 功能向 F1 屬性包(屬性包前綴.關鍵字和註冊表中首碼的線上網址)發出值:F1 向瀏覽器發送 VSP URL+ 參數。

- 可視化工作室功能(語言編輯器、可視化工作室特定功能表項等):F1 向瀏覽器發送視覺工作室 URL。

使用說明檢視器預設幫助內容來源設定為本地端說明時(在說明檢視器中啟動):

- VSP 具有 F1 屬性包和本地儲存索引(即屬性包前綴.關鍵字 = 本地儲存索引中找到的值)之間的關鍵字匹配功能:F1 呈現説明查看器中的主題。

- 可視化工作室功能(VSP 沒有選項可以覆蓋從 Visual Studio 功能發出的屬性包):F1 在説明查看器中呈現視覺工作室主題。

設置以下註冊表值,以便為供應商幫助內容啟用 F1 回退。 F1 回退意味著説明查看器設置為連線尋找 F1 幫助內容,並且供應商內容在本地安裝到使用者的硬碟驅動器上。 説明查看器應查看內容的本地説明,即使預設設置用於連線説明。

1. 在説明 2.3 註冊表鍵下設定**供應商內容**值:

   - 對於 32 位元作業系統:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "供應商內容"=dword:0000001

   - 對於 64 位元作業系統:

        HKEY_LOCAL_MACHINE_SOFTWARE_Wow6432Node_微軟\幫助\v2.3_目錄_VisualStudio15

        "供應商內容"=dword:0000001

2. 在説明 2.3 註冊表項下註冊合作夥伴命名空間:

   - 對於 32 位元作業系統:

      HKEY_LOCAL_MACHINE_SOFTWARE_微軟\説明\v2.3_合作夥伴<em>\\<命名空间\></em>

      "位置"="離機"

   - 對於 64 位元作業系統:

      HKEY_LOCAL_MACHINE_軟體_哇6432Node_微軟\説明\v2.3_合作夥伴<em>\\<命名空间\></em>

      "位置"="離機"

**基本本機命名空間解析**

要打開基本本機命名空間解析,在註冊表中添加一個新的 DWORD 名稱:BaseNativeNamespace 並將其值設置為 1(在他們想要支援的目錄鍵下)。  例如,如果要使用 Visual Studio 目錄,則可以將密鑰新增到路徑:

HKEY_LOCAL_MACHINE_SOFTWARE_Wow6432Node_微軟\幫助\v2.3_目錄_VisualStudio15

當遇到格式為「HEADER/METHOD」的 F1 關鍵字時,將解析「/」字元,從而生成以下建構:

- 標題:是可用於在註冊表中註冊的命名空間

- 方法:這將成為傳遞的關鍵字。

例如,給定一個名為自訂庫的自訂庫和一個稱為 MyTestMethod 的方法,當 F1 請求進來`CustomLibrary/MyTestMethod`時,它將格式化為 。

然後,用戶可以將自定義庫註冊為合作夥伴配置單元下的命名空間,並提供所需的任何位置鍵,傳遞給查詢的關鍵字將是 MyTestMethod。

**在 IDE 中開啟說明除錯工具**

新增以下註冊表項和值:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER_軟體\微軟_VisualStudio_15.0\動態説明**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER_軟體\微軟_VisualStudio_16.0\動態説明**

::: moniker-end

值:在零售資料中顯示除錯輸出:是

在 IDE 中,在"説明"功能表項下,選擇 **「調試説明上下文**」。

**內容中繼資料**

在下表中,括弧之間出現的任何字串都是必須替換為已識別值的占位符。 例如,在元\<名中="Microsoft.Help.Locale"內容="[語言代碼]"/>,"語言代碼"必須替換為"en-us"等值。

| 屬性 (HTML 表示) | 描述 |
| - | - |
| \<元名稱="Microsoft.Help.Locale"內容="[語言代碼]"/> | 設置此主題的區域設置。 如果此標記在主題中使用,則必須只使用一次,並且必須插入任何其他 Microsoft 幫助標記上方。 如果未使用此標記,則通過使用與產品區域設置關聯的斷字器(如果指定)對主題的正文文本進行索引;否則,使用 en-us 斷字元。 此標記符合 ISOC RFC 4646。 為確保 Microsoft 説明正常工作,請使用此屬性而不是常規語言屬性。 |
| \<元名稱="微軟.説明.主題本地"內容="[語言代碼]"/> | 在也使用其他區域設置時,為本主題設置區域設置。 如果此標記在主題中使用,則只能使用一次。 當目錄包含多種語言的內容時,使用此標記。 目錄中的多個主題可以具有相同的 ID,但每個主題必須指定唯一的主題區域設置。 指定與目錄區域設置匹配的 TopicLocale 的主題是顯示在目錄中的主題。 但是,主題的所有語言版本都顯示在搜尋結果中。 |
| \<標題>[標題]\</標題> | 指定本主題的標題。 此標記是必需的,並且必須在主題中只使用一次。 如果主題的正文不包含標題\<div> 部分,則此標題將顯示在主題和目錄中。 |
| \<元名稱="微軟.説明.關鍵字"內容"[關鍵字短語]"/> | 指定在幫助檢視器的索引窗格中顯示的連結的文字。 按下連結時,將顯示主題。 您可以為主題指定多個索引關鍵字,或者如果不希望指向此主題的鏈接顯示在索引中,則可以省略此標記。 早期版本的「幫助」關鍵字可以轉換為此屬性。 |
| \<元名="微軟.説明.Id"內容"[主題ID]"/> | 設置本主題的標識碼。 此標記是必需的,並且必須在主題中只使用一次。 ID 必須在目錄中具有相同區域設置的主題中唯一。 在另一個主題中,您可以使用此 ID 建立指向此主題的連結。 |
| \<元名稱="微軟.説明.F1"內容="[系統.Windows.控制.原始.I回收專案容器生成器]"/> | 指定此主題的 F1 關鍵字。 您可以為主題指定多個 F1 關鍵字,或者如果不希望在應用程式使用者按 F1 時顯示此主題,則可以省略此標記。 通常,只為主題指定一個 F1 關鍵字。 早期版本的「幫助」關鍵字可以轉換為此屬性。 |
| \<元名稱="描述"內容="[主題描述]"/> | 提供本主題中內容的簡短摘要。 如果此標記在主題中使用,則只能使用一次。 查詢庫直接訪問此屬性;它不存儲在索引檔中。 |
| 元名="微軟.説明.Tocparent"內容"[parent_Id]"/> | 在內容表中指定此主題的父主題。 此標記是必需的,並且必須在主題中只使用一次。 該值是父值的Microsoft.Help.Id。 主題在目錄中只能有一個位置。 "-1"被視為目錄根的主題 ID。 在[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]中,該頁是説明查看器主頁。 這也是我們專門將 TocParent_-1 添加到某些主題以確保它們顯示在頂層的原因。 説明查看器主頁是系統頁面,因此不可替換。 如果 VSP 嘗試新增 ID 為 -1 的頁面,它可能會增加到內容集中,但說明檢視器將始終使用系統頁面 - 說明瀏覽者首頁 |
| \<元名稱="微軟.説明.Tocorder"內容="[正整數]"/> | 指定此主題相對於其對等主題在目錄中顯示的位置。 此標記是必需的,並且必須在主題中只使用一次。 值為整數。 指定較低值整數的主題顯示在指定較高值整數的主題的上方。 |
| \<元名稱="微軟.幫助.產品"內容="[產品代碼]"/> | 指定本主題介紹的產品。 如果此標記在主題中使用,則只能使用一次。 此資訊也可以作為傳遞給説明索引器的參數提供。 |
| \<元名稱="微軟.説明.ProductVersion"內容="[版本號]"/> | 指定本主題介紹的產品版本。 如果此標記在主題中使用,則只能使用一次。 此資訊也可以作為傳遞給説明索引器的參數提供。 |
| \<元名稱="微軟.幫助.類別"內容="[字串]"/> | 產品用於標識內容的子部分。 您可以為主題標識多個子節,或者如果不希望鏈接標識任何子節,則可以省略此標記。 此標記用於存儲從早期版本的幫助轉換主題時,用於存儲 TargetOS 和 TargetFrameworkMoniker 的屬性。 內容的格式為屬性名稱:屬性值。 |
| \<元名稱="微軟.説明.主題版本內容"[主題版本號]"/> | 指定目錄中存在多個版本的主題的此版本。 由於Microsoft.Help.Id不保證是唯一的,因此當目錄中存在多個主題版本時,例如,當目錄包含 .NET Framework 3.5 的主題和 .NET Framework 4 的主題且兩者具有相同的Microsoft.Help.Id時,需要此標記。 |
| \<元名="自品牌"內容"[真實或FALSE]"/> | 指定此主題是使用説明庫管理器啟動品牌包還是特定於主題的品牌包。 此標記必須為 TRUE 或 FALSE。 如果為 TRUE,則關聯主題的品牌包將覆蓋説明庫管理器啟動時設置的品牌包,以便即使主題與其他內容的呈現不同,也會按預期呈現。 如果是 FALSE,則根據説明庫管理器啟動時設置的品牌包呈現當前主題。 默認情況下,説明庫管理器假定自品牌為 false,除非自品牌變數聲明為 TRUE;否則,説明庫管理器假定自品牌為 false。因此,您不必聲明\<元名稱=「自品牌」內容=「FALSE」/>。 |

## <a name="create-a-branding-package"></a>建立品牌包

Visual Studio 版本包含許多不同的視覺工作室產品,包括可視化工作室合作夥伴的隔離和集成外殼。  這些產品中的每一個都需要一定程度的基於主題的幫助內容品牌支援,這是產品獨有的。  例如,Visual Studio 主題需要具有一致的品牌展示,而包裝 ISO Shell 的 SQL Studio 需要為每個主題提供自己獨特的幫助內容品牌。  集成的殼牌合作夥伴可能希望他們的幫助主題位於父 Visual Studio 產品幫助內容中,同時保持自己的主題品牌。

品牌包由包含説明查看器的產品安裝。  對於視覺工作室產品:

- 説明查看器 2.3\<應用根目錄(例如:C:程式檔 (x86)\Microsoft 説明查看器\v2.3)中安裝了回退品牌包(Branding_區域設置>.mshc)。  這用於未安裝產品品牌包(未安裝任何內容)或已安裝的品牌包已損壞的情況。  使用應用根回退品牌包時,將忽略 Visual Studio 元素(徽標和反饋)。

- 從內容包服務安裝 Visual Studio 內容時,還會安裝品牌包(這是首次安裝內容方案)。  如果品牌包有更新,則在下一次內容更新或其他包安裝操作發生時將安裝更新。

Microsoft 幫助查看器支援基於主題元數據的主題品牌。

- 當主題元數據定義自品牌 = true 時,呈現主題原樣,不執行任何操作(至於品牌)。

- 當主題元數據定義自品牌 = false 時,請使用與主題供應商元數據值關聯的品牌包。

- 當主題元數據定義名稱="Microsoft.Help.Topicvendor"內容*\<供應商 MSHA>中的品牌包名称时,請使用內容值中定義的品牌包。

- 在可視化工作室目錄中,有品牌包的優先應用。  首先應用 Visual Studio 預設品牌,然後,如果在主題元數據中定義並受關聯的品牌包(如安裝 msha 中定義)支援,則供應商定義的品牌將應用為覆蓋。

品牌元素通常分為三個主要類別:

- 標題元素(範例包括回饋連結、條件免責聲明文本、徽標)

- 內容行為 (例如展開/ 折疊控制元件文字元素與代碼段元素)

- 頁腳元素(範例版權)

被視為品牌元素的專案包括(本規範中詳細規定):

- 目錄/產品徽標(示例,視覺工作室)

- 回饋連結及電子郵件元素

- 免責宣告文字

- 版權文字

視覺化工作室說明檢視器品牌套件中的支援檔包括:

- 圖形(徽示、圖示等)

- 品牌.js - 支援內容行為的文稿檔

- 品牌.xml - 跨目錄內容一致使用的字串。  注意:對於品牌中的 Visual Studio 當地語系化\<文本元素,請包括 _locID\">的唯一值"

- 品牌.css - 表示一致性的樣式定義

- 列印.css - 用於列印簡報的樣式定義

如上所述,品牌包與主題相關聯:

- 在中繼資料中定義自品牌 = false 時,主題將繼承目錄品牌包

- 或者,當自品牌 = false,並且在 MSHA 中定義了唯一的品牌包,並在安裝內容時可用

對於實現自定義品牌包(VSP 內容、自品牌=True)的 VSP,一種方法是從回退品牌包開始(隨説明查看器一起安裝),並根據需要更改檔的名稱。  Branding_\<區域設置>.mshc 檔案是一個 zip 檔案,檔副檔名更改為 .mshc,因此只需將擴展名從 .mshc 更改為 .zip 並提取內容即可。  請參閱下文,瞭解品牌包元素並根據需要進行修改(例如,將徽標更改為 VSP 徽標,以及品牌.xml 檔中對徽標的引用、根據 VSP 細節更新品牌.xml 等)。

完成所有修改後,創建包含所需品牌元素的 zip 檔,並將副檔名更改為 .mshc。

要關聯自定義品牌包,請創建 MSHA,其中包含對品牌 mshc 檔的引用以及內容 mshc(包含主題)。  有關如何創建基本 MSHA,請參閱下面的"MSHA"。

當主題包含\<元名稱\"Microsoft.Help.Help.自品牌"內容\"false"/>时,Branding.xml 檔包含用於一致呈現主題中特定專案的元素清單。  下面列出了"品牌.xml"檔中元素的可視化工作室清單。  此清單旨在用作 ISO 殼牌採用者的範本,他們在此修改這些元素(例如徽標、反饋和版權),以滿足他們自己的產品品牌需求。

注意...「{n}」指定的變數具有代碼依賴項 - 刪除或更改這些值將導致錯誤,並可能導致應用程式崩潰。 可視化工作室品牌包中包括本地化標識符(示例_locID="代碼段.n")。

**品牌.xml**

| | |
| - | - |
| 功能： | **可摺疊區域** |
| 使用︰ | 展開摺疊內容控制文字 |
| **Element** | **ReplTest1** |
| 展開文字 | 展開 |
| 折疊文字 | 摺疊 |
| 功能： | **代碼段** |
| 使用︰ | 代碼段控制文本。  注意:具有"非中斷"空間的代碼片段內容將更改為空格。 |
| **Element** | **ReplTest1** |
| 複製到剪貼簿 | 複製至剪貼簿 |
| 檢視顏色文字 | 檢視著色 |
| 組合VBTab顯示語言 | 視覺基礎 (範例) |
| VB 宣告 | 宣告 |
| VB使用 | 使用量 |
| 功能： | **回饋、頁腳和徽標** |
| 使用︰ | 提供回饋控制,以便客戶透過電子郵件提供有關當前主題的回饋。  內容的版權文本。  徽標定義。 |
| **Element** | **值(可以修改這些字串以滿足內容採用者的需求。** |
| 版權 | © 2013 Microsoft Corporation。 著作權所有，並保留一切權利。 |
| 傳送回饋 | \<href=">{0}{1}向微軟發送\<關於 此主題的反饋/>。 |
| 回饋連結 | |
| 徽標標題 | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| 徽標檔案名稱 | vs_logo_bk.gif |
| 標誌檔案名稱HC | vs_logo_wh.gif |
| 功能： | **免責聲明** |
| 使用︰ | 一組針對計算機翻譯內容的特定於案例的免責聲明。 |
| **Element** | **ReplTest1** |
| MT_Editable | 本文已翻譯為機器。 如果您有網路連接,請選擇「連線查看此主題」以可編輯模式查看此頁面,同時使用原始英語內容。 |
| MT_NonEditable | 本文已翻譯為機器。 如果您有網路連接,請選擇「連線查看此主題」以可編輯模式查看此頁面,同時使用原始英語內容。 |
| MT_QualityEditable | 本文已手動翻譯。 如果您有網路連接,請選擇「連線查看此主題」以可編輯模式查看此頁面,同時使用原始英語內容。 |
| MT_QualityNonEditable | 本文已手動翻譯。 如果您有網路連接,請選擇「連線查看此主題」以可編輯模式查看此頁面,同時使用原始英語內容。 |
| MT_BetaContents | 本文已翻譯為初步版本。 如果您有網路連接,請選擇「連線查看此主題」以可編輯模式查看此頁面,同時使用原始英語內容。 |
| MT_BetaRecycledContents | 本文已手動翻譯為初步版本。 如果您有網路連接,請選擇「連線查看此主題」以可編輯模式查看此頁面,同時使用原始英語內容。 |
| 功能： | **連結表** |
| 使用︰ | 支援線上主題連結 |
| **Element** | **ReplTest1** |
| 連結表標題 | 連結表 |
| 主題EnuLink文字 | 查看電腦上可用的本\<主題的英文版本 />。 |
| 主題線上文字 | 檢視此主題\<href="{0} {1} \<「>線上 /> |
| 線上文字 | 線上 |
| 功能： | **視訊音訊控制** |
| 使用︰ | 顯示視訊內容的元素與文字 |
| **Element** | **ReplTest1** |
| 不支援多媒體 | 必須安裝 IE9 或{0}更高支援 內容。 |
| 視訊文字 | 顯示視訊 |
| 音訊文字 | 流音訊 |
| 線上視訊連結文字 | \<p>要查看與此主題關聯的視頻,請{0}\<單擊 href="{1}">{2}此處\</>。\</p> |
| 線上音訊連結文字 | \<p>要收听与此主题关联的音频,請按{0}\<兩下 href=">{1}{2}此處\</>。\</p> |
| 功能： | **內容未安裝控制** |
| 使用︰ | 包含內容未安裝內容的文字元素(字串) |
| **Element** | **ReplTest1** |
| 內容未安裝標題 | 您的電腦上找不到任何內容。 |
| 內容未安裝 下載內容文字 | \<p>要將內容\<下載到 您的{0}電腦{1},>单击 "\<管理"選項卡 />"\</p> |
| 內容未安裝文字 | \<p>计算机上未安装任何内容。 有關本地説明內容安裝,請與管理員聯繫。\</p> |
| 功能： | **主題找不到控制項** |
| 使用︰ | 顯示主題的文字元素(字串) |
| **Element** | **ReplTest1** |
| 主題找不到標題 | 在電腦上找不到請求的主題。 |
| 主題找不到瀏覽線上文字 | \<p\<>您请求的主题在计算机上找不到 ,但您可以創建 href="{0}">{1}連線\</>查看主题。\</p> |
| 主題 找不到下載內容文字 | \<p>檢視瀏覽窗格,瞭解指向類似\<主題的連結 ,或{0}{1}"href"">\<按下"管理 '選項卡/>将内容下载到计算机。\</p> |
| 主題找不到文字 | \<p>您请求的主题在计算机上找不到。\</p> |
| 功能： | **主題損壞控制** |
| 使用︰ | 用於成像主題損毀.htm 的文字元素(字串) |
| **Element** | **ReplTest1** |
| 主題已損壞的標題 | 無法顯示請求的主題。 |
| 主題已損毀圖線上文字 | \<p>帮助查看器无法显示请求的主题。 主題的內容或基礎系統依賴項中可能存在錯誤。\</p> |
| 功能： | **首頁控制項** |
| 使用︰ | 支援顯示說明檢視器頂級節點內容的文字。 |
| **Element** | **ReplTest1** |
| HomePageTitle | 說明檢視者首頁 |
| 首頁簡介 | \<p>欢迎加入 Microsoft 幫助查看器,這是使用 Microsoft 工具、產品、技術和服務的每個人的重要資訊來源。 説明查看器允許您訪問訪問訪問方式和參考資訊、範例代碼、技術文章等。 要查找所需的內容,請瀏覽目錄、使用全文搜索或使用關鍵字索引流覽內容。\</p> |
| 首頁內容安裝文字 | \<p \<>br\<{0}/>使用{1}\<href=">管理内容/>选项卡执行以下操作\<:ul \<>li>将内容添加到您的计算机。\</li \<>li>检查本地内容的更新。\</li \<>li>从您的计算机中删除内容。\</li \<>/ul>\</p> |
| 首頁已安裝書書 | 已安裝的書籍 |
| 首頁 沒有書書安裝 | 您的電腦上找不到任何內容。 |
| 首頁說明設定 | 說明內容設定 |
| 首頁說明設定文字 | \<p>您当前的设置是本地帮助。 説明查看器顯示電腦上已安裝的內容。\<br />要更改"説明"內容的來源,請在 Visual\<Studio{0}功能表欄上 選擇"\<跨樣式"">幫助,設置説明首選項/跨>。\<br />\</p> |
| 兆 位元組 | MB |

**品牌.js**

品牌.js 檔包含 Visual Studio 説明查看器品牌元素使用的 JavaScript。  下面是品牌元素和支援的 JavaScript 函數的清單。  此檔案要當地語系化的所有字串都在此文件頂部的"可本地化字串"部分定義。  已為品牌.js 檔中的 loc 字串創建了 ICL 檔。

||||
|-|-|-|
|**品牌功能**|**JavaScript 函數**|**說明**|
|無 功。。。||定義變數|
|取得使用者代碼語言|設定使用者偏好設定|將索引 # 映射到代碼語言|
|設定與取得 Cookie 值|得到餅乾,設置餅乾||
|繼承成員|變更成員標籤|展開/折疊繼承成員|
|當自品牌=假|上載荷|讀取查詢字串以檢查該字串是否為列印請求。  設置所有代碼段以集中使用者首選選項卡。 如果是列印請求,則設置為「印表機友好」設置為 true。 檢查對比度過高模式。|
|代碼段|新增特定文字語言標記集||
||從 Devlang 取得索引||
||變更選項卡||
||設定片段片段||
||設定電流朗||
||複製到剪貼簿||
|可摺疊區域|新增到可折疊控制集|將所有可摺疊控制件物件寫入清單。|
||CA_Click|基於可摺疊區域的狀態,定義要呈現的影像和文字|
|對徽標的對比支援|是黑色背景()|調用以確定背景是否為黑色。  僅在高對比度模式下準確。|
||是高對比度()|使用彩色範圍偵測高對比模式|
||上高對比度(黑色)|偵測到高對比時呼叫|
|LST 功能|||
||新增放大縮小字型功能 放大縮小字型功能||
||更新 LST(電流朗)||
||取得Devlang從代碼片段(朗)||
|多媒體功能|標題(開始、結束、文字、樣式)||
||尋找所有媒體控制(規範化 ID)||
||取得活動播放器(規範化 ID)||
||標題OnOff(id)||
||到秒(t)||
||取得所有評論(節點)||
||樣式更正(樣式名稱、樣式值)||
||顯示CC(id)||
||副標題(ID)||

**HTM 檔案**

品牌包包含一組 HTM 檔,這些檔支援將關鍵資訊傳達給幫助內容使用者的方案,例如,主頁包含描述已安裝的內容集的部分,以及告知使用者在本地主題集中找不到主題時告知使用者的頁面。 每個產品都可以修改這些 HTM 檔。  ISO 殼牌供應商能夠採用預設品牌包,並更改這些頁面的行為和內容,以滿足其需求。  這些檔引用其各自的品牌包,以便品牌標籤從品牌.xml 檔中獲取相應的內容。

||||
|-|-|-|
|**檔案**|**使用**|**顯示的內容來源**|
|首頁.htm|這是一個頁面,顯示當前安裝的內容,以及適合向使用者展示其內容的任何其他消息。  此檔具有附加的元資料屬性"Microsoft.Help.Id"內容="-1",該屬性將此內容置於本地內容 TOC 的頂部。||
||<META_HOME_PAGE_TITLE_ADD/>|品牌.xml,標記\<主頁標題>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|品牌.xml,標記\<主頁介紹>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|品牌.xml,標記\<主頁內容安裝文字>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|標題部分品牌.xml\<標籤 HomePage 安裝簿>,\<從應用程式生成 的數據,HomePageNoBooks 安裝>未安裝書籍。|
||<HOME_PAGE_SETTINGS_SECTION_ADD/>|標題部分品牌.xml\<標籤主頁説明設置>,節\<文本 主頁幫助設置文本>。|
|主題損壞.htm|當本地集中存在主題,但由於某種原因無法顯示(損壞的內容)。||
||<META_TOPIC_CORRUPTED_TITLE_ADD/>|品牌.xml,標籤\<主題損壞標題>|
||<TOPIC_CORRUPTED_SECTION_ADD/>|品牌.xml,標籤\<主題損壞查看線上文字>|
|主題未發現.htm|在本地內容集中找不到主題,也連線不可用||
||<META_TOPIC_NOT_FOUND_TITLE_ADD/>|品牌.xml,標籤\<主題未找到標題>|
||<META_TOPIC_NOT_FOUND_ID_ADD/>|品牌.xml,標籤\<主題找不到查看線上文字> \<+ 主題找不到下載內容文字>|
||<TOPIC_NOT_FOUND_SECTION_ADD/>|品牌.xml,標籤\<主題找不到文字>|
|內容未安裝.htm|當產品未安裝本地內容時。||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|品牌.xml,標記\<內容未安裝標題>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD/>|品牌.xml,標記\<內容未安裝下載內容文字>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD/>|品牌.xml,標記\<內容未安裝文字>|

**CSS 檔案**

可視化工作室説明檢視器品牌包包含兩個 css 檔,以支援一致的可視化工作室幫助內容演示文稿:

- 品牌.css - 包含用於成像自品牌\false 的 css 元素

- 印表機.css - 包含用於成像自品牌=false 的 cs 元素

Branding.css 檔包括 Visual Studio 主題演示文稿的定義\<(警告是Branding_ 區域設置中包含的品牌.css>.mshc 從包服務可能會更改)。

**圖像檔案**

可視化工作室內容顯示視覺工作室徽標以及其他圖形。  "可視化工作室説明查看器"品牌包中的圖形檔的完整清單如下所示。

||||
|-|-|-|
|**檔案**|**使用**|**範例**|
|清除.gif|用於成成可折疊區域||
|footer_slice.gif|頁腳演示||
|info_icon.gif|顯示資訊時使用|免責聲明|
|online_icon.gif|此圖示將與連線連結關聯||
|選項卡左BD.gif|用於呈現程式碼段容器||
|tabRightBD.gif|用於呈現程式碼段容器||
|vs_logo_bk.gif|用於品牌.xml 標\<記 LogoFilename>中定义的正常对比度徽标引用。  對於 Visual Studio 產品,徽標名稱為 vs_logo_bk.gif。||
|vs_logo_wh.gif|用於品牌.xml\<標籤 LogoFileNameHC>中定义的正常高徽标引用。  對於 Visual Studio 產品,徽標名稱為 vs_logo_wh.gif。||
|ccOff.png|字幕圖形||
|ccOn.png|字幕圖形||
|影像Sprite.png|用於成成可折疊區域|展開或折疊圖形|

## <a name="deploy-a-set-of-topics"></a>部署一組主題

這是一個簡單而快速的教程,用於創建由 MSHA 檔和包含主題的駕駛室或 MSHC 集組成的幫助查看器內容部署集。 MSHA 是一個 XML 檔,用於描述一組駕駛室或 MSHC 檔。 幫助查看器可以讀取 MSHA 以獲取內容清單(。CAB 或 。可用於本地安裝的 MSHC 檔)。

這隻是描述説明查看器 MSHA 非常基本的 XML 架構的入門部分。  此簡要概述和示例説明內容安裝程式.msha 下方有一個示例實現。

MSHA 的名稱(出於此引瑟)而言,是 HelpContentSetup.msha(檔的名稱可以是任何內容,具有副檔名。MSHA)。 幫助內容設置.msha(下面的範例)應包含可用的駕駛室或 MSHC 的清單。  檔案類型必須在 MSHA 中保持一致(不支援 MSHA 和 CAB 檔案類型的組合)。 對於每個 CAB 或 MSHC,應該有\<一個 div 類=「包」>...\</div>(參見下面的範例)。

注意:在下面的實施示例中,我們包括了品牌包。 這對於獲取所需的 Visual Studio 內容呈現元素和內容行為至關重要。

範例説明內容安裝程式.msha 檔:(將"內容集名稱 1"和"內容集名稱 2"等替換為檔名。

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

1. 創建本地資料夾,如"C:\sample內容"

2. 在此範例中,我們將使用 MSHC 檔來包含主題。  MSHC 是 zip,檔案副檔名從 .zip 更改為 。MSHC。

3. 將下面的幫助內容安裝程式.msha 創建為文本檔(記事本用於創建檔案),並將其保存到上述指定資料夾(請參閱步驟 1)。

類"品牌"存在且是唯一的。 品牌 mshc 包含在此入門中,以便已安裝的內容具有品牌,並且 MSHC 中包含的內容行為將包含品牌包中包含的相應支援元素。 如果沒有這一點,當系統查找不屬於翻錄(已安裝)內容的支援項時,將導致錯誤。

要取得 Visual Studio 品牌包,請將 Branding_en-US.mshc 檔(C:*程式檔 (x86)\Microsoft 説明查看器\v2.3]複製到您的工作資料夾。

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

使用和擴展上述步驟將使 VSP 能夠為可視化工作室説明查看器部署其內容集。

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>向視覺化工作室外殼添加説明(整合和隔離)

**簡介**

本演練演示如何將幫助內容合併到 Visual Studio 外殼應用程式中,然後部署它。

**需求**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [視覺工作室 2013 孤立殼牌紅人](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**概觀**

命令[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]列程式是 IDE[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]的版本,您可以基於該版本來建立應用程式。 此類應用程式包含隔離外殼以及您創建的擴展。 使用[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]SDK 中包含的隔離外殼專案範本生成擴展。

建立基於孤立外殼的應用程式及其説明的基本步驟:

1. 獲取[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]ISO 外殼可再分發(微軟下載)。

2. 在 Visual Studio 中,創建基於隔離外殼的幫助擴展,例如,本演練稍後將介紹的 Contoso 幫助擴展。

3. 將擴展和 ISO Shell 可再分發包裝到部署 MSI(應用程式設置)。 本演練不包括設置步驟。

創建視覺化工作室內容儲存。 對於整合的外殼方案,將 Visual Studio12 更改為產品目錄名稱,如下所示:

- 創建資料夾 C:\程式資料\微軟\説明庫2_目錄\VisualStudio15。

- 建立名為 CatalogType.xml 的檔案並將其添加到資料夾中。 該檔案應包含以下代碼行:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

定義註冊表中的內容存儲。 對於整合外殼,將 VisualStudio15 更改為產品目錄名稱:

- HKLM_SOFTWARE_Wow6432Node_微軟_説明\v2.3_目錄_VisualStudio15

   鍵:位置路徑字串值:C:\程序數據\微軟\説明庫2_目錄_VisualStudio15]

- HKLM_SOFTWARE_Wow6432Node_微軟_說明\v2.3_目錄_VisualStudio15_en-US

   鍵:目錄名稱字串值:[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]文件

**建立項目**

要建立隔離的 Shell 延伸:

1. 在視覺工作室中,在 **「檔**」下,選擇 **「新專案**」,在 **「其他項目類型」** 下選擇 **「擴充性**」,然後選擇 **「視覺工作室外殼隔離**」。。 命名專案`ContosoHelpShell`),以基於可視化工作室隔離外殼範本創建擴充性專案。

2. 在解決方案資源管理器中,在ContosoHelpShellUI專案中,在「資源檔」資料夾中打開應用程式命令.vsct。 確保此行已註釋掉(搜尋"No_Help"):`<!-- <define name="No_HelpMenuCommands"/> -->`

3. 選擇要編譯和運行**調試**的 F5 鍵。 在隔離 Shell IDE 的實驗實例中,選擇 **「説明」** 選單。 確保顯示 **「查看説明**」、**添加和刪除幫助內容**以及**設定幫助首選項**命令。

4. 在解決方案資源管理器中,在ContosHelpShell專案中,在「殼體自訂」資料夾中打開 ContosoHelpShell.pkgdef。 要定義 Contoso 幫助目錄,請添加以下行:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. 在解決方案資源管理器中,在 ContosHelpShell 專案中,在「殼體自訂」資料夾中打開 ContosoHelpShell.應用程式.pkgdef。 要啟用 F1 説明,添加以下行:

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

6. 在「解決方案資源管理器」中,在 ContosoHelpShell 解決方案的上下文選單中,選擇 **「屬性」** 功能表項。 在 **「設定屬性**」 選單選擇**設定管理員**。 在 **「設定」** 欄中,將每個「調試」值更改為"釋放」。。

7. 建置方案。 這將在發佈資料夾中創建一組檔,將在下一節中使用。

要測試此項,就像已部署一樣:

1. 在要部署到的電腦上,安裝下載的(從上面)ISO 外殼。

2. 在\\#程序 檔案 (x86)\\`Contoso`中建立一個 資料夾,並命名為它。

3. 將內容從 ContosoHelpShell 版本資料夾\\複製到 [程式檔 (x86)\Contoso] 資料夾。

4. 通過在 **「開始」** 選單`Regedit`中選擇 **「執行**」並輸入啟動註冊表編輯器。 在註冊表編輯器中,選擇 **「檔案**」,然後**匯入**。 瀏覽到 ContosoHelpShell 專案資料夾。 在 ContosoHelpShell 子資料夾中,選擇 ContosoHelpShell.reg。

5. 建立內容儲存:

    對 ISO Shell - 建立 Contoso 內容儲存 C:\程式資料\微軟_說明庫2_目錄\ContosoDev12

    對於[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]整合外殼,建立資料夾 C:\程式資料\微軟\説明庫2_目錄\VisualStudio15

6. 建立目錄類型.xml 並新增到內容儲存(上一步),其中包含:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. 新增以下註冊表項:

    HKLM_SOFTWARE_Wow6432Node_微軟_説明\v2.3_目錄_VisualStudio15鍵:位置路徑字串值:

    對於 ISO 外殼:

    C:程序數據微軟説明圖書館2目錄視覺工作室15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]集成外殼:

    C:程序數據微軟説明圖書館2目錄視覺工作室15en-美國

    鍵:目錄名稱字串值:[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]文檔。 對於 ISO 外殼,這是目錄的名稱。

8. 將內容(駕駛室或 MSHC 和 MSHA)複製到本地資料夾。

9. 用於測試內容存儲的集成外殼命令行。 對於 ISO 外殼,根據需要更改目錄和啟動應用值以匹配產品。

     "C:_程式檔 (x86)\微軟幫助查看器\v2.3_HlpViewer.exe" /目錄名稱 VisualStudio15 /幫助查詢方法="頁&id_ContosoTopic0" /啟動應用程式微軟,VisualStudio,12.0

10. 啟動 Contoso 應用程式(從 Contoso 應用根目錄)。 在 ISO 外殼中,選擇 **「説明」** 選單項,並將 **「設定幫助首選項」** 更改為 **「使用本地説明**」 。

11. 在 shell 中選擇 **「說明」** 選單項目,然後**查看說明**。 本地説明查看器應啟動。 選擇「**管理內容**」 選項卡。在 **「安裝來源**」下,選擇 **「磁碟**」選項按鈕。 選擇 **...** 按鈕並瀏覽到包含 Contoso 內容的本地資料夾(複製到上述步驟中的本地資料夾)。 選擇幫助內容設定.msha。 康托索現在應該在書選中作為一本書出現。 選擇 **'新增**',然後選擇 **'按鈕**(右下角)。

12. 在 Contoso IDE 中,選擇 F1 鍵以測試 F1 功能。

## <a name="additional-resources"></a>其他資源

有關執行時 API,請參閱[Windows 說明 API](/previous-versions/windows/desktop/helpapi/helpapi-portal)。

有關如何利用說明 API 的詳細資訊,請參考[檢視器碼範例](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)。

您可以提交[有關開發人員社區的](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)功能建議。
