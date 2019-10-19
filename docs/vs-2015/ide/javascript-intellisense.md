---
title: JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 67
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39c90a8550736c945f04467e9366a73039cfa2b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670482"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense 藉由在您撰寫程式碼的同時提供資訊，幫助您更快速地撰寫程式碼，並減少錯誤。 當您在 JavaScript 編輯器中使用用戶端指令碼時，IntelliSense 會根據目前的內容列出可用的物件、函式、屬性及參數。 您可以從 IntelliSense 提供的快顯清單選取程式碼撰寫選項，以完成程式碼。

 IntelliSense 可讓您更輕鬆地完成下列工作：

- 尋找成員資訊。

- 直接將語言項目插入程式碼中。

- 不需離開程式碼編輯器即可維護內容。

- 支援自訂 IntelliSense 與 XML 文件註解，以及 JavaScript IntelliSense 擴充性。

  此主題包括下列章節：

- [判斷 IntelliSense 的內容](#DeterminingIntelliSenseContext)

- [處理 IntelliSense 資訊](#ProcessingIntelliSenseInformation)

- [JavaScript IntelliSense 功能](#Features)

- [JavaScript IntelliSense 擴充性](#Extensibility)

- [JavaScript 驗證](#Validation)

  如需 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 之 IntelliSense 功能的詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。

## <a name="DeterminingIntelliSenseContext"></a> 判斷 IntelliSense 的內容
 JavaScript IntelliSense 會根據您目前的指令碼內容相關的所有指令碼，提供程式碼撰寫的選擇。 這包括目前檔案內的指令碼項目。 它同時也包含任何從指令碼直接參考或間接參考的程式碼，例如：指令碼檔參考、組件 (Assembly) 指令碼參考、服務參考和關聯頁面參考。

 您目前的指令碼內容會根據下列項目而建立：

- 在使用中文件內所有指令碼區塊中定義的函式。 具有 .aspx.、.ascx、.master、.html 和 .htm 等副檔名的檔案所支援之內嵌 (Inline) 指令碼區塊。

- 具有指向另一個指令碼檔案之 `script` 屬性的 `src` 元素。 目標指令碼檔必須以 .js 為副檔名。

- 以 `reference` 指示詞參考其他 JavaScript 檔案的 JavaScript 檔。

- 全域物件、IntelliSense 擴充功能或延遲載入指令碼檔案的參考群組。

- XML Web 服務的參考。

- 如果 Web 應用程式是一個支援 AJAX 的 ASP.NET 應用程式則為 <xref:System.Web.UI.ScriptManager> 和 <xref:System.Web.UI.ScriptManagerProxy> 控制項。

- [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)] (如果您使用的是具備 AJAX 能力的 ASP.NET Web 應用程式)。

    > [!NOTE]
    > IntelliSense 不支援在 HTML 項目上使用事件處理常式屬性的指令碼，或定義於 `href` 屬性的指令碼。

## <a name="ProcessingIntelliSenseInformation"></a> 處理 IntelliSense 資訊
 為了提供 JavaScript IntelliSense，語言服務會執行下列作業：

- 根據主動式文件 (Active Document) 內的參考建立 JavaScript 相依檔案清單，並遞迴地檢查參考之檔案的指令碼參考。

- 周遊清單並從每個檔案收集類型資訊，以及其他相關資料。

- 彙總資料，並將資料傳遞至 JavaScript 語言服務，讓 IntelliSense 可以使用類型資訊和資料。

- 監控可能影響 IntelliSense 清單的檔案變更，並視需要更新清單。 遠端存放區上的指令碼 (例如使用 HTTP 參考的那些指令碼) 不會受到監視。

## <a name="Features"></a> JavaScript IntelliSense 功能
 JavaScript IntelliSense 支援下列物件：

- [文件物件模型 (DOM) 元素](#HTMLDom)

- [內建物件](#IntrinsicObjects)

- [使用者定義的變數、函式和物件](#UserDefined)

- 使用[指令碼參考](#Script)、[參考指示詞](#ReferenceDirectives)和[參考群組](#ReferenceGroups)等參考在外部檔案中定義的物件。

- 在經由 Visual Studio 下載的遠端檔案中定義的物件。

- 在 [XML 文件註解](#XMLDocComments)中指定的物件，例如參數和欄位。

- 使用標準 JavaScript 註解標記 (//) 描述的物件。 如需詳細資訊，請參閱[擴充 JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)。

- 使用 [JavaScript IntelliSense 擴充性](#Extensibility)機制支援的物件。 如需詳細資訊，請參閱[擴充 JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)。

- [ASP.NET AJAX 物件](#ASPNet)

  當 IntelliSense 無法決定物件的類型時，它會利用使用中文件中的識別項提供陳述式完成的選項。 如需詳細資訊，請參閱[識別項的陳述式完成](../ide/statement-completion-for-identifiers.md)。

### <a name="HTMLDom"></a> HTML DOM 元素
 JavaScript IntelliSense 提供動態超文字標記語言 (DHTML) DOM 項目的程式設計參考，例如：`body`、`form` 和 `div`。 IntelliSense 只會顯示包含在目前文件內的項目和主版頁面 (Master Page)。 JavaScript IntelliSense 也支援 `window` 和 `document` 物件及其成員。

### <a name="IntrinsicObjects"></a> 內建物件
 JavaScript IntelliSense 提供了內建物件 `Array`、`String`、`Math`、`Date` 和 `Number` 的程式設計參考。 如需有關內建物件的詳細資訊，請參閱[標準的內建物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects)。

### <a name="UserDefined"></a> 使用者定義的變數、函式和物件
 變更 JavaScript 檔時，[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 會掃描已開啟及已參考的文件，以判斷所有可用的程式碼資源。 這包括您建立的變數、函式和物件。 隨後 JavaScript IntelliSense 便可以使用這些資源。

 如需使用者定義之變數、函式和物件的詳細資訊，請參閱 MSDN 網站上的[建立您自己的物件](http://go.microsoft.com/fwlink/?LinkId=108671)。

### <a name="External"></a> 外部檔案參考
 您可以加入外部檔案參考的各種類型，以便在您的程式碼中提供 IntelliSense 支援。 外部檔案參考可能是指令碼參考、參考指示詞或是使用參考群組指定。

#### <a name="Script"></a> 指令碼參考
 除了在網頁內撰寫所有用戶端指令碼之外，您還可以參考包含指令碼的外部檔案。 這種方式可以很方便的在各個網頁間重複使用程式碼，並且可讓瀏覽器快取用戶端指令碼。

 如果您目前未使用具備 ASP.NET AJAX 能力的網頁，則可以使用 `src` 項目之開頭標記內的 `script` 屬性參考外部指令碼檔。 `src` 屬性指定了包含原始程式碼或資料之外部檔案的 URL。

 下列範例顯示在 <`script`> 標記 (Tag) 內使用 `src` 屬性來參考指令碼檔的標記 (Markup)。

```html
<script type="text/javascript" src="~/Scripts/JavaScript.js">

</script>
```

 如果您正在使用具有 ASP.NET AJAX 能力的網頁，則可以使用 <xref:System.Web.UI.ScriptReference> 控制項的 <xref:System.Web.UI.ScriptManager> 物件參考指令碼檔。

 下列範例顯示了以 <xref:System.Web.UI.ScriptReference> 控制項內的 <xref:System.Web.UI.ScriptManager> 物件來參考指令碼檔的標記。

```html
<asp:ScriptManager ID="ScriptManager1" runat="server">
  <Scripts>
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />
  </Scripts>
</asp:ScriptManager>
```

 IntelliSense 也支援在 ASP.NET AJAX Web 應用程式內的組件中，內嵌為資源的指令碼檔。 如需內嵌指令碼資源的詳細資訊，請參閱[逐步解說：將 JavaScript 檔案內嵌為組件中的資源](https://msdn.microsoft.com/library/d8cb78cd-95a9-4dc6-92df-391866817e89)。

#### <a name="ReferenceDirectives"></a> Reference 指示詞
 `reference` 指示詞可讓 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 在您目前正編輯的指令碼和其他指令碼之間，建立關聯性 (Relationship)。 `reference` 指令詞可讓您在目前指令碼檔的指令碼內容中包含指令碼檔。 如此可讓 IntelliSense 參考外部定義的函式、類型及欄位，將其當做您的程式碼使用。

 您可以以 XML 註解的格式建立 `reference` 指示詞。 指示詞在檔案內的宣告必須早於任何指令碼。 `reference` 指示詞可以包含磁碟架構的指令碼參考、組件架構的指令碼參考、服務架構的指令碼參考，或網頁架構的指令碼參考。

 列下範例示範使用磁碟架構之 reference 指示詞。 在第一個範例中，語言服務會在與包含專案檔 (例如，.jsproj) 相同的資料夾中尋找檔案。

 `/// <reference path="ScriptFile1.js" />`

 `/// <reference path="Scripts/ScriptFile2.js" />`

 `/// <reference path="../ScriptFile3.js" />`

 `/// <reference path="~/Scripts/ScriptFile4.js" />`

 下列範例示範如何建立組件架構指令碼的參考。

 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`

 下列範例示範如何建立服務架構指令碼的參考：

 `/// <reference path="MyService.asmx" />`

 `/// <reference path="Services/MyService.asmx" />`

 `/// <reference path="../MyService.asmx" />`

 `/// <reference path="~/Services/MyService.asmx" />`

> [!NOTE]
> JavaScript IntelliSense 不支援內含在 Web 應用程式專案 (WAP) 之 Web 服務 (.asmx) 檔案中的指令碼。

 下列範例示範如何建立網頁架構指令碼的參考。

 `/// <reference path="Default.aspx" />`

 `/// <reference path="Admin/Default.aspx" />`

 `/// <reference path="../Default.aspx" />`

 `/// <reference path="~/Admin/Default.aspx" />`

 `reference` 指示詞有下列規則。

- `reference` XML 註解必須在任何指令碼之前宣告。

- 您必須使用具有三個斜線的 XML 註解語法。 使用標準註解語法 (兩個斜線) 建立的參考會被忽略。

- 每個指示詞只能指定一個檔案或參考。

- 不允許有多個網頁架構指令碼的參考。

- 如果已指定某個網頁參考，則不允許再使用其他類型的 reference 指示詞。

- 檔案名稱使用相對路徑。 您可以使用波狀符號運算子 (`~`) 代表應用程式根目錄的相對路徑。

- 絕對路徑會被忽略。

- 參考之網頁內的 Reference 指示詞將不會被處理，這表示 reference 指示詞不會遞迴地解析網頁。 只會納入直接由網頁所參考的指令碼。

#### <a name="ReferenceGroups"></a> 參考群組
 您可以使用預先定義的參考群組指定特殊 IntelliSense .js 檔案於不同 JavaScript 專案範圍中。 下列為可用的參考群組類型：

- 隱含 (Windows)，適用於使用 JavaScript 的 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式。 這個群組中包含的檔案會在程式碼編輯器中針對指定類型之專案開啟的每一個 .js 檔案範圍中。

- 隱含 (Web)，適用於 HTML5 專案。 這個群組中包含的檔案會在程式碼編輯器中針對這些專案類型開啟的每一個 .js 檔案範圍中。

- 專屬的背景工作參考群組，適用於 HTML5 Web 背景工作。 在這個群組中指定的檔案會在具有專屬背景工作參考群組之明確參考的 .js 檔案範圍中。

- 泛型，適用於其他 JavaScript 專案類型。

  在大部分情況下，您不需要修改參考群組。 不過，如果您要進行變更，可以使用 JavaScript 程式碼編輯器的設定選項來指定參考群組中的檔案。 如需使用這項功能的相關指示，請參閱[選項、文字編輯器、JavaScript、IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md)。

> [!TIP]
> IntelliSense 參考通常是用來為全域物件和 IntelliSense [擴充功能](#Extensibility)提供 IntelliSense 支援。 您也可以為必須在執行階段使用指令碼載入器載入的指令碼使用這項功能。

### <a name="remote-file-references"></a>遠端檔案參考
 您可以指示 Visual Studio 下載 JavaScript 檔案中參考的遠端 JavaScript 檔案，以便為遠端檔案或程式庫提供 IntelliSense 支援。 當您使用此功能時，檔案會在您將它們包含在 JavaScript 檔案中做為參考時下載。

> [!NOTE]
> 除了 Web 專案之外，這項功能僅適用於在專案的內容之外開啟的 JavaScript 檔案。 Web 專案預設會下載專案中參考的遠端檔案。

 如需使用這項功能的相關指示，請參閱[選項、文字編輯器、JavaScript、IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md)。

> [!WARNING]
> 如果啟用了此功能，並觀察到程式碼編輯器的效能變慢，建議您將它停用。

### <a name="XMLDocComments"></a> XML 文件註解
 XML 文件註解是您加入至指令碼的程式碼項目文字描述。 這些文字描述會在您參考註解指令碼時，在 IntelliSense 中顯示。 例如，您可以提供函式的參數和傳回值的相關資訊。 XML 文件註解僅能從參考的檔案、組件和服務取得。 如需詳細資訊，請參閱 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)和[建立 XML 文件註解](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)。

 IntelliSense 也可以在下列情況顯示 XML 文件註解：

- 參考另一個 .js 檔的 .js 檔案。

- 參考 .aspx 檔的 .js 檔案。

- 參考 .js 檔的 .aspx 檔案。

  當 .aspx 檔案參考另一個 .aspx 檔時，便無法使用 IntelliSense。

### <a name="ASPNet"></a> ASP.NET AJAX 物件
 ASP.NET AJAX 也支援 JavaScript IntelliSense。 ASP.NET AJAX 包含了用戶端架構，可擴充 ECMAScript (JavaScript) 內所提供的標準類型。 為了讓 JavaScript IntelliSense 提供與 ASP.NET AJAX 物件有關的詳細資料，在整個 [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)] 中已加入了 XML 文件註解。 這些 XML 文件註解會在您使用 ASP.NET AJAX Library 內含的類型及成員時顯示。

> [!NOTE]
> JavaScript IntelliSense 不會顯示私用成員。 私用成員在 ASP.NET AJAX 中是以底線 (_) 為起始的成員來代表。

## <a name="Extensibility"></a> JavaScript IntelliSense 擴充性
 JavaScript 語言服務提供的物件和函式，可讓您為使用協力廠商程式庫的開發人員改變 IntelliSense 經驗。 當預設語言服務無法提供您要為客戶提供的所有資訊時，這些功能特別有用。 如需詳細資訊，請參閱[擴充 JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)。

## <a name="Validation"></a> JavaScript 驗證
 JavaScript 指令碼驗證通常會在背景中執行。 當 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 在 JavaScript 程式碼中偵測到語法錯誤時，會以下列方式提供意見：

- 將編輯器內的項目加上底線。 以紅色波浪底線指出錯誤。 如果您將滑鼠指標停留在錯誤上方，則會顯示錯誤描述的工具提示。

- [錯誤清單]  視窗。 [錯誤清單]  視窗會顯示錯誤描述、發生錯誤的檔案位置、行號和欄數，以及專案。 若要顯示 [錯誤清單]  視窗，請按一下 [檢視]  功能表中的 [錯誤清單]  。

- [輸出] 視窗會顯示未載入的參考。

## <a name="see-also"></a>另請參閱
- [使用 IntelliSense](../ide/using-intellisense.md)
- [產生 XML 文件註解](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)
- [擴充 JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)
- [識別項的陳述式完成](../ide/statement-completion-for-identifiers.md)
- [XML 文件註解](../ide/xml-documentation-comments-javascript.md)
- [關於 DHTML 物件模型](http://go.microsoft.com/fwlink/?LinkID=92344) \(英文\)
- [列出成員](https://msdn.microsoft.com/1b9cc469-9cd4-4d42-9999-1f9479635ff8) \(機器翻譯\)
- [SRC 屬性 &#124; src 屬性](http://go.microsoft.com/fwlink/?LinkId=92345)