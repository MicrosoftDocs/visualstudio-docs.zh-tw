---
title: 擴充 JavaScript IntelliSense |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94e2186fa13f7fe125457dc6f04d6d31d0bcc65d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046119"
---
# <a name="extending-javascript-intellisense"></a>擴充 JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript IntelliSense 擴充性功能可讓您自訂在協力廠商程式庫的 JavaScript 編輯器中 IntelliSense 結果。 這可以改善開發人員使用這些程式庫的體驗。  
  
 JavaScript 語言服務會提供 IntelliSense 功能新增至專案的第三方 JavaScript 程式庫。 對於大部分的程式庫，提供陳述式完成自動語言服務。 下圖顯示陳述式完成的範例：  
  
 ![陳述式完成範例](../ide/media/js-intellisense-completion.png "js_intellisense_completion")  
  
 如果您的程式庫所含的變數、 函式和物件的描述中標準 JavaScript 註解標記 (/ /)，就會自動獲益，根據預設，從 IntelliSense 擴充性功能，提供描述性資訊在快顯方塊中的，右邊的項目在完成清單中，或當您輸入函式呼叫中的左括弧隨即出現。 快顯方塊中的註解包含成員的描述。 下列範例顯示完成清單的快顯方塊。  
  
 ![快速諮詢 pop 的範例&#45;方塊](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")  
  
 若要進一步改善開發人員體驗，您可能要快顯方塊中的開發人員提供類型資訊。 您可以使用 JavaScript 來提供類型資訊[XML 文件註解](../ide/xml-documentation-comments-javascript.md)而不是標準的註解標記。 您可以使用三個斜線註解標記 （/ /） 和一組定義的 XML 項目，以加入 XML 文件註解。  
  
 或者，您可以使用 JavaScript IntelliSense 擴充性來提供類型資訊。 這項功能可讓您建立 JavaScript 延伸模組，並將它們新增至指令碼內容來自訂 IntelliSense 結果。 擴充功能，也就是 JavaScript 檔案，在您訂閱所公開的事件`intellisense`語言服務的物件。 JavaScript IntelliSense 擴充性是常用的解決方案，程式庫，如果文件庫中的行為模式，讓 JavaScript 語言服務無法提供所需的層級的 IntelliSense 支援，而且如果宣告式 XML 的替代項目文件註解，也需要。 藉由自訂 IntelliSense 結果，您可以建立第一級的 IntelliSense 體驗，無論任何可能會限制語言服務的預設功能的行為模式為何。 如需詳細資訊，請參閱 <<c0> [ 識別項的陳述式完成](../ide/statement-completion-for-identifiers.md)。  
  
## <a name="adding-an-extension-to-the-script-context"></a>將延伸模組新增至指令碼內容  
 IntelliSense 擴充功能執行，它必須新增至目前的指令碼內容。 擴充功能可以自動新增至指令碼內容的自動探索機制，或您可以將延伸加入至指令碼內容以手動方式使用參考群組或參考指示詞。  
  
 自動探索機制可讓語言服務會自動尋找延伸模組，請依照檔案命名慣例*libraryname*。 intellisense.js，且位於與程式庫相同的目錄這會套用擴充功能。 例如，jQuery 程式庫是有效的副檔名會是 jQuery.intellisense.js。 更嚴格的 jQuery 的擴充功能，您可以使用檔案的名稱，例如 jQuery 1.7.1.intellisense.js （版本特定擴充功能） 或 jQuery.ui.intellisense.js （已設定領域的 jQuery 程式庫的擴充功能）。 如果指定的程式庫找到一個以上的延伸模組，會使用限制性最高版本的延伸模組。  
  
 如果您想要使用所有 JavaScript 專案檔的擴充功能，您可能會改為選擇加入參考群組中的延伸模組。 有數種類型的參考群組，可能是其中包含隱含的參考以及包含專用背景工作的參考。 若要新增延伸模組，您通常需要將檔案新增為隱含的參考群組，請**隱含 (Windows)**，**隱含 (Web)**。 隱含的參考是在程式碼編輯器中開啟每一個.js 檔案範圍中。 當您使用這個方法時，您需要新增擴充功能和擴充功能補充檔案。  
  
 使用**IntelliSense**頁**選項**對話方塊，即可將延伸模組新增為參考群組。 您可以存取**IntelliSense**頁面上，選擇**工具**，**選項**功能表列上，然後選擇**文字編輯器**， **JavaScript**， **IntelliSense**，**參考**。 如需參考群組的詳細資訊，請參閱[JavaScript IntelliSense](../ide/javascript-intellisense.md)並[選項、 文字編輯器、 JavaScript、 IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md)。  
  
 如果您想要使用一組特定的檔案的擴充功能，請使用參考指示詞。 當您使用這個方法時，您需要參考擴充功能和擴充功能補充檔案。 如需使用參考指示詞的詳細資訊，請參閱[JavaScript IntelliSense](../ide/javascript-intellisense.md)。  
  
## <a name="handling-intellisense-events"></a>處理 IntelliSense 事件  
 擴充功能可讓您藉由訂閱事件這類自訂 IntelliSense 結果`statementcompletion`事件的語言服務`intellisense`物件。 下列範例顯示簡單的延伸模組，可由其語言服務以隱藏從陳述式完成以底線開頭的成員。 此程式碼包含在 underscorefilter.js 並處於\\ \\ *Visual Studio 安裝路徑*\JavaScript\References 資料夾。  
  
```javascript  
intellisense.addEventListener('statementcompletion', function (event) {  
    if (event.targetName === "this") return;  
  
    var filterRegex;  
  
    if (event.target === undefined || event.target === window)  
        filterRegex = /^_.*\d{2,}/;  
    else  
        filterRegex = /^_.*/;  
  
    event.items = event.items.filter(function (item) {  
        return !filterRegex.test(item.name);  
    });  
});  
```  
  
 在上述程式碼中，延伸模組會檢查[targetName 屬性](#TargetName)並[目標屬性](#Target)的屬性`statementcompletion`事件物件，例如排除物件`this`和`window`，並確保可以識別有效的陳述式完成清單。 如果可以識別完成清單，延伸模組更新陳述式完成[項目屬性](#Items)篩選出以底線開頭的成員集合。  
  
 如需其他範例，查看\\ \\ *Visual Studio 安裝路徑*\JavaScript\References 資料夾。 ShowPlainComments.js 檔案，此資料夾中的提供使用標準 JavaScript 註解標記提供預設的 IntelliSense 支援的其他事件的範例 (/ /)。 Underscorefilter.js，例如 showPlainComments.js 已做為工作擴充功能，可使用，並在您的程式碼中使用註解標記，變數、 函式和物件時，您可以看到產生的 IntelliSense 資訊。 如需其他範例，請參閱 <<c0> [ 程式碼範例](#CodeExamples)。  
  
> [!WARNING]
>  如果您修改包含在 Visual Studio 的延伸模組檔案，您可能會停用 JavaScript IntelliSense 或延伸模組支援的功能。  
  
 在 延伸模組程式碼，您可以建立下列事件類型的處理常式使用`addEventListener`:  
  
- `statementcompletion`其中會加入陳述式完成事件處理常式。 陳述式完成提供一份之後輸入特殊字元像是句號 （.），就會出現的特定類型的成員或識別碼的清單會顯示您輸入時，或當您按下 CTRL + J。處理常式會接收事件物件的型別`CompletionEvent`，可支援下列成員：[屬性的項目](#Items)，[目標屬性](#Target)， [targetName 屬性](#TargetName)，並[範圍屬性](#Scope)。  
  
- `signaturehelp`其中會加入處理常式，如 IntelliSense 參數資訊。 參數資訊，可讓您的數目、 名稱和所需的函式參數類型的相關資訊。 處理常式會接收事件物件的型別`SignatureHelpEvent`，可支援下列成員：[目標屬性](#Target)， [parentObject 屬性](#ParentObject)， [functionComments 屬性](#FunctionComments)， [functionHelp 屬性](#FunctionHelp)。  
  
- `statementcompletionhint`其中會加入處理常式，如 IntelliSense 快速諮詢。 [快速諮詢] 快顯方塊會顯示程式碼中之識別碼的完整宣告。 處理常式會接收事件物件的型別`CompletionHintEvent`，可支援下列成員： [completionItem 屬性](#CompletionItem)，以及[symbolHelp 屬性](#SymbolHelp)。  
  
  如需範例，顯示 IntelliSense 功能，例如陳述式完成、 參數資訊，以及快速的資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。  
  
> [!NOTE]
>  在 JavaScript 中，快速諮詢是指右邊的完成清單會出現快顯方塊。 無法以手動方式叫用 快速諮詢。  
  
## <a name="intellisenseObject"></a> intellisense 物件  
 下表顯示可供函式`intellisense`物件。 `intellisense`物件是只能在設計階段可用。  
  
|功能|描述|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|加入 IntelliSense 事件的事件處理常式。<br /><br /> `type` 是字串值。 有效值包括 `statementcompletion`、`signaturehelp` 和 `statementcompletionhint`。<br /><br /> `handler` 會接收下列類型之一的事件物件的事件處理常式函式：<br /><br /> -   `CompletionEvent`用於`statementcompletion`事件。<br />-   `SignatureHelpEvent`用於`signaturehelp`事件。<br />-   `CompletionHintEvent`用於`statementcompletionhint`事件。<br /><br /> 如需使用此函式的範例，請參閱[程式碼範例](#CodeExamples)。|  
|`annotate(obj, doc);`|將文件註解，從一個物件複製到另一個物件，指定物件的文件。<br /><br /> `obj` 指定要複製的文件的物件。<br /><br /> `doc` 指定要複製的文件的物件。<br /><br /> 如需示範如何使用此函式的範例，請參閱 <<c0> [ 新增 IntelliSense 註解](#Annotations)。|  
|`getFunctionComments(func);`|傳回指定的函式的註解。<br /><br /> `func` 指定為其傳回註解的函式。<br /><br /> 您可以設定`func`參數使用`completionItem.value`。<br /><br /> 傳回`functionComments`物件包含下列成員： `above`， `inside`，和`paramComment`。 如需詳細資訊，請參閱 < [functionComments 屬性](#FunctionComments)屬性。<br /><br /> `getFunctionComments` 可以只從呼叫的事件處理常式註冊的其中一個內`addEventListener`。<br /><br /> 如需示範如何使用此函式的範例，請參閱 < \\ \\ *Visual Studio 安裝路徑*\JavaScript\References\showPlainComments.js。|  
|`logMessage(msg);`|將診斷訊息傳送至 [輸出] 視窗中。<br /><br /> `msg` 是包含訊息的字串。<br /><br /> 如需示範如何使用此函式的範例，請參閱 <<c0> [ 傳送訊息至 [輸出] 視窗](#Logging)。|  
|`nullWithCompletionsOf(value);`|傳回特殊 null 值的完成清單取決於傳入的物件`value`參數。<br /><br /> `value` 決定傳回值的完成清單。 `value` 可以是任何類型。<br /><br /> 傳回 null 值會被視為 null 在設計階段功能，而傳回值的完成清單的完成清單相同`value`參數。<br /><br /> 此函式的用法之一是提供傳回值的 IntelliSense 時的傳回型別是在執行階段，可預測，但是傳回的值為`null`在設計階段。|  
|`redirectDefinition(func, definition);`|指示時要使用提供的定義函式而不是原始的 func 函式參數說明 IntelliSense 或**移至定義**要求。<br /><br /> `func` 指定目標函式。<br /><br /> `definition` 指定的參數資訊，而不是在目標函式使用的函式和**移至定義**。|  
|`setCallContext(func, thisArg);`|設定範圍中針對指定的函式的呼叫內容。<br /><br /> `func` 指定要設定範圍的函式。<br /><br /> `thisArg` 是一種物件常值的`this`關鍵字可參考，以指定成員的新範圍。 您也可以包含引數来傳入此參數，例如， `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` 提供行為類似於`Function.prototype.bind`，只不過它只用於設計階段 IntelliSense 支援。 您可以使用`setCallContext`來設定函式範圍，如果您要模擬呼叫程式碼，否則無法連線，如此當您呼叫此函式，函式呼叫就會包含正確的範圍和引數。|  
|`undefinedWithCompletionsOf(value);`|傳回特殊的完成清單取決於傳入的物件未定義的值`value`參數。<br /><br /> `value` 決定傳回值的完成清單。 `value` 可以是任何類型。<br /><br /> 未定義傳回值處理為未定義在設計階段，但完成的傳回值的清單是相同的完成清單`value`參數。<br /><br /> 此函式的用法之一是當傳回的型別是在執行階段，可預測，但傳回的值未定義在設計階段時，傳回值提供 IntelliSense。|  
|`version()`|傳回 Visual Studio 版本。|  
  
## <a name="event-members"></a>事件成員  
 下列各節描述下列事件的事件物件中公開的成員： `statementcompletion`， `signaturehelp`，和`statementcompletionhint`。  
  
### <a name="CompletionItem"></a> completionItem 屬性  
 傳回的識別碼，稱為完成項，其要求快速諮詢 快顯方塊中。 這個屬性可供`statementcompletionhint`事件物件，以及[屬性的項目](#Items)屬性`statementcompletion`事件物件。  
  
 傳回值：`completionItem`物件  
  
 以下是成員`completionItem`物件：  
  
- `name`. 讀取/寫入時用於`items`集合; 否則為唯讀。 傳回識別完成項的字串。  
  
- `kind`. 讀取/寫入時用於`items`集合; 否則為唯讀。 傳回字串，表示完成項目類型。 可能的值是方法、 欄位、 屬性、 參數、 變數，並保留。  
  
- `glyph`. 讀取/寫入時用於`items`集合; 否則為唯讀。 傳回字串，表示會顯示完成清單中的圖示。 可能值`glyph`使用下列格式： vs:*glyphType*，其中*glyphType*對應中的語言無關成員<xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>列舉型別。 例如，`vs:GlyphGroupMethod`是一個可能值`glyph`。 當`glyph`未設定，`kind`屬性會決定預設圖示。  
  
- `parentObject`. 唯讀。 傳回父物件。  
  
- `value`. 唯讀。 傳回物件，表示完成項目的值。  
  
- `comments`. 唯讀。 傳回包含變數的欄位上方的註解的字串。  
  
- `scope`. 唯讀。 傳回完成項目的範圍。 可能的值為全域、 本機、 參數和成員。  
  
### <a name="Items"></a> 項目屬性  
 取得或設定陣列，這些陳述式完成項目。 陣列中的每個項目是[completionItem 屬性](#CompletionItem)物件。 `items`屬性可供`statementcompletion`事件物件。  
  
 傳回值： 陣列  
  
### <a name="FunctionComments"></a> functionComments 屬性  
 傳回此函式的註解。 這個屬性可供`signaturehelp`事件物件。  
  
 傳回值：`comments`物件  
  
 以下是成員`comments`物件：  
  
- `above`. 傳回的函式上方的註解。  
  
- `inside`. 傳回在函數中，註解通常 VSDoc 格式。  
  
- `paramComments`. 傳回陣列，表示函式中每個參數的註解。 陣列的成員包括：  
  
    - `name`. 傳回字串，表示參數名稱。  
  
    - `comment`. 傳回字串，包含參數的註解。  
  
### <a name="FunctionHelp"></a> functionHelp 屬性  
 傳回的函式的說明。 這個屬性可供`signaturehelp`事件物件。  
  
 傳回值：`functionHelp`物件  
  
 以下是成員`functionHelp`物件：  
  
- `functionName`. 讀取/寫入。 傳回包含函式名稱的字串。  
  
- `signatures`. 讀取/寫入。 取得或設定陣列，這些函式簽章。 陣列中的每個項目是`signature`物件。 有些`signature`屬性，例如`locid`，對應到通用[XML 文件註解](../ide/xml-documentation-comments-javascript.md)屬性。  
  
     成員`signature`物件包括：  
  
    - `description`. 讀取/寫入。 傳回字串，描述函式。  
  
    - `locid`. 讀取/寫入。 傳回字串識別項，其中包含此函式的當地語系化資訊。  
  
    - `helpKeyword`. 讀取/寫入。 傳回字串，包含的 Help 關鍵字。  
  
    - `externalFile`. 讀取/寫入。 傳回字串，表示檔案，其中包含為成員識別碼。  
  
    - `externalid`. 讀取/寫入。 傳回字串，表示函式的成員識別碼。  
  
    - `params`. 讀取/寫入。 取得或設定函式的參數陣列。 參數陣列中的每個項目是`parameter`的屬性會對應至的下列屬性的物件[ \<param >](../ide/param-javascript.md)項目：  
  
        - `name`. 讀取/寫入。 傳回字串，表示參數名稱。  
  
        - `type`. 讀取/寫入。 傳回字串，表示參數類型。  
  
        - `elementType`. 讀取/寫入。 如果類型是`Array`，傳回字串，表示陣列中元素的型別。  
  
        - `description`. 讀取/寫入。 傳回描述參數的字串。  
  
        - `locid`. 讀取/寫入。 傳回字串識別項，其中包含此函式的當地語系化資訊。  
  
        - `optional`. 讀取/寫入。 傳回字串，表示參數是否為選擇性。 `true` 指出參數是選擇性的。`false`指出它不是。  
  
    - `returnValue`. 讀取/寫入。 取得或設定下列屬性的傳回值具有屬性的物件相對應[\<傳回 >](../ide/returns-javascript.md)項目：  
  
        - `type`. 讀取/寫入。 傳回字串，表示傳回型別。  
  
        - `elementType`. 讀取/寫入。 如果類型是`Array`，傳回字串，表示陣列中元素的型別。  
  
        - `description`. 讀取/寫入。 傳回描述的傳回值的字串。  
  
        - `locid`. 讀取/寫入。 傳回字串識別項，其中包含此函式的當地語系化資訊。  
  
        - `helpKeyword`. 讀取/寫入。 傳回字串，包含的 Help 關鍵字。  
  
        - `externalFile`. 讀取/寫入。 傳回字串，表示檔案，其中包含為成員識別碼。  
  
        - `externalid`. 讀取/寫入。 傳回字串，表示函式的成員識別碼。  
  
### <a name="ParentObject"></a> parentObject 屬性  
 傳回父物件的成員函式。 例如，對於`document.getElementByID`，`parentObject`傳回`document`物件。 這個屬性可供`signaturehelp`事件物件。  
  
 傳回值： 物件  
  
### <a name="Target"></a> 目標屬性  
 傳回物件，表示觸發程序的字元，也就是句號 （.） 左邊的項目。 對於函式，`target`傳回要求的參數資訊的函式。 這個屬性可供`statementcompletion`和`signaturehelp`事件物件。  
  
 傳回值： 物件  
  
### <a name="TargetName"></a> targetName 屬性  
 傳回字串，表示目標。 例如，對於"this"，`targetName`傳回"this"。 "A.B 」 （當資料指標之後"B"），如`targetName`傳回"B"。 這個屬性可供`statementcompletion`事件物件。  
  
 傳回值： 字串  
  
### <a name="SymbolHelp"></a> symbolHelp 屬性  
 傳回要求的快速諮詢 快顯方塊中的完成項。 這個屬性可供`statementcompletionhint`事件物件。  
  
 傳回值：`symbolHelp`物件。  
  
 某些屬性`symbolHelp`物件，例如`locid`，對應到通用[XML 文件註解](../ide/xml-documentation-comments-javascript.md)屬性。  
  
 以下是成員`symbolHelp`物件：  
  
- `name`. 讀取/寫入。 傳回字串，包含識別項名稱。  
  
- `symbolType`. 讀取/寫入。 傳回字串，表示符號類型。 可能值包括未知、 布林值、 數字、 字串、 物件、 函式、 陣列、 日期和 Regex。  
  
- `symbolDisplayType`. 讀取/寫入。 傳回字串，包含要顯示的型別名稱。 如果`symbolDisplayType`未設定，`symbolType`用。  
  
- `elementType`. 讀取/寫入。 如果`symbolType`是`Array`，傳回字串，表示陣列中元素的型別。  
  
- `scope`. 讀取/寫入。 傳回字串，表示符號的範圍。 可能值包括全域、 本機、 參數和成員。  
  
- `description`. 讀取/寫入。 傳回字串，包含符號的描述。  
  
- `locid`. 讀取/寫入。 傳回包含符號的當地語系化資訊的字串識別項。  
  
- `helpKeyword`. 讀取/寫入。 傳回字串，包含的 Help 關鍵字。  
  
- `externalFile`. 讀取/寫入。 傳回字串，表示檔案，其中包含為成員識別碼。  
  
- `externalid`. 讀取/寫入。 傳回字串，表示符號的成員識別碼。  
  
- `functionHelp`. 讀取/寫入。 傳回[functionHelp 屬性](#FunctionHelp)，其中可能包含資訊時`symbolType`是函式。  
  
### <a name="Scope"></a> 範圍屬性  
 傳回事件的完成範圍。 完成的可能值範圍為全域和成員。 這個屬性可供`statementcompletion`事件物件。  
  
 傳回值： 字串  
  
## <a name="debugging-intellisense-extensions"></a>偵錯 IntelliSense 擴充功能  
 您無法偵錯擴充功能，但您可以使用[intellisense 物件](#intellisenseObject)函式，將資訊傳送至 Visual Studio [輸出] 視窗。 如需示範如何使用此函式的範例，請參閱 <<c0> [ 傳送訊息至 [輸出] 視窗](#Logging)本主題稍後的。 針對`logMessage`運作，必須註冊至少一個事件處理常式延伸模組中。  
  
## <a name="CodeExamples"></a> 程式碼範例  
 本節包含示範如何使用 IntelliSense 擴充性 Api 的程式碼範例。 另外還有其他方式使用這些 Api。 如需其他範例，請參閱中的下列檔案\\ \\ *Visual Studio 安裝路徑*\JavaScript\References 資料夾。 這些使用 JavaScript 語言服務所使用的範例。  
  
- underscoreFilter.js。 此程式碼會隱藏來自 IntelliSense 的私用成員。 它包含的事件處理常式`statementcompletion`事件。  
  
- showPlainComments.js。 此程式碼會提供 IntelliSense 支援，標準的註解。 它包含的事件處理常式`signaturehelp`和`statementcompletionhint`事件。  
  
### <a name="Annotations"></a> 加入 IntelliSense 註解  
 下列程序示範如何提供協力廠商程式庫中的 IntelliSense 文件支援，而不需直接修改程式庫。 若要這樣做，您可以使用`intellisense.annotate`延伸模組中。  
  
 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:  
  
- demoLib.js，是代表協力廠商程式庫的專案檔。  
  
- demoLib.intellisense.js，是 IntelliSense 擴充功能。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。  
  
- 這個 appCode.js 是代表應用程式程式碼的專案檔。  
  
##### <a name="to-add-an-intellisense-annotation"></a>將 IntelliSense 註解  
  
1. 將下列程式碼新增至 demoLib.js 中。  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2. 將下列程式碼新增至 demoLib.intellisense.js 中。  
  
    ```javascript  
    intellisense.annotate(someFunc, function (a) {  
        /// <signature>  
        /// <summary>Description of someFunc</summary>  
        /// <param name="a">Param a</param>  
        /// </signature>  
    });  
  
    intellisense.annotate(window, {  
        // This is a comment on a global variable named rectangle.  
        rectangle: undefined  
    });  
    ```  
  
3. 加入下列參考指示詞，做為 appCode.js 的第一行。 這裡使用的路徑表示 JavaScript 檔案在同一個資料夾中。  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4. 在 appCode.js 中，輸入以下程式碼。 您會看到顯示為 IntelliSense 的 參數資訊的延伸模組中的 XML 文件註解。  
  
     ![Intellisense.annotate 的使用範例](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")  
  
5. 在 appCode.js 中，輸入以下程式碼。 雖然您輸入時，您會看到標準的註解中顯示為 IntelliSense 快速諮詢的延伸模組。  
  
     ![Intellisense.annotate 的使用範例](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")  
  
### <a name="Logging"></a> 將訊息傳送至 [輸出] 視窗  
 下列程序示範如何將訊息傳送至 [輸出] 視窗。 您可以傳送訊息，以協助偵錯 IntelliSense 延伸模組。  
  
 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:  
  
- exampleLib.js，是代表協力廠商程式庫的專案檔。  
  
- exampleLib.intellisense.js，是 IntelliSense 擴充功能。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。  
  
- 這個 appCode.js 是代表應用程式程式碼的專案檔。  
  
##### <a name="to-send-a-message-to-the-output-window"></a>若要將訊息傳送至輸出視窗  
  
1. 將下列程式碼新增至 exampleLib.js 中。  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2. 將下列程式碼新增至 exampleLib.intellisense.js 中。  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        // Prints out statement completion info: Either (1) the member   
        // list, if the trigger character was typed, or (2) the   
        // statement completion identifiers.  
        // e.target represents the object left of the trigger character.  
        intellisense.logMessage(  
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');  
  
        // Prints out all statement completion items.  
        e.items.forEach(function (item) {  
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);  
        });  
    });  
    ```  
  
3. 加入下列參考指示詞，做為 appCode.js 的第一行。 這裡使用的路徑表示 JavaScript 檔案在同一個資料夾中。  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4. 在 [輸出] 視窗中，選擇**JavaScript Language Service**中**顯示輸出來源**清單。 (若要檢視 [輸出] 視窗，請選取**輸出**從 [檢視] 功能表。)  
  
5. 在 appCode.js 中，輸入以下程式碼。 雖然您輸入時，[輸出] 視窗會顯示訊息的語言服務。 在 [輸出] 視窗中的第一個訊息指出已要求在目前範圍的陳述式完成。  
  
    ```javascript  
    some  
    ```  
  
     以下是您應該會看到輸出的部分檢視。  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6. 選擇**全部清除**輸出 視窗中的按鈕。  
  
7. 輸入下列程式碼。 在 [輸出] 視窗中的第一個訊息指出已經要求之成員的清單。  
  
    ```javascript  
    someVar.  
    ```  
  
     以下是您應該會看到輸出的部分檢視：  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
### <a name="Icons"></a> 變更 IntelliSense 圖示  
 下列程序示範如何變更預設顯示 intellisense 的圖示。 當您提供相關文件庫特有的概念，例如命名空間、 類別、 介面和列舉的 IntelliSense 資訊時，這可能是很有用。  
  
 可用的圖示值，請參閱<xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>。  
  
 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:  
  
- exampleLib.js，也就是專案的檔案該 represens 協力廠商程式庫。  
  
- exampleLib.intellisense.js，是 IntelliSense 擴充功能。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。  
  
- 這個 appCode.js 是代表應用程式程式碼的專案檔。  
  
##### <a name="to-change-the-icons"></a>若要變更圖示  
  
1. 將下列程式碼新增至 exampleLib.js 中。  
  
    ```javascript  
    function Namespace(name) {  
        this._isNamespace = true;  
        window[name] = this;  
    };  
  
    function Enum(values) {  
        var e = Object.create(values);  
        e._isEnum = true;  
        return e;  
    };  
  
    var SomeNamespace = new Namespace('SomeNamespace');  
    // A constructor function is considered a class.  
    SomeNamespace.SomeClass1 = function () { }  
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });  
    ```  
  
2. 將下列程式碼新增至 exampleLib.intellisense.js 中。  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        e.items.forEach(function (item) {  
            // Detect a namespace by using the _isNamespace flag.  
            if (item.value && item.value._isNamespace) {  
                item.glyph = 'vs:GlyphGroupNamespace';  
                }  
  
            if (item.parentObject && item.parentObject._isNamespace) {  
                // The item is a member of a namespace.   
  
                // All constructor functions that are part of a namespace   
                // are considered classes.   
                // A constructor function starts with  
                // an uppercase letter by convention.    
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()   
                    == item.name[0])) {  
                    item.glyph = 'vs:GlyphGroupClass';  
                }  
  
                // Detect an enumeration by using the _isEnum flag.  
                if (item.value && item.value._isEnum) {  
                    item.glyph = 'vs:GlyphGroupEnum';  
                }  
            }  
        });  
    });  
  
    intellisense.addEventListener('statementcompletionhint', function (e) {  
        if (e.completionItem.value) {  
            if (e.completionItem.value._isNamespace) {  
                e.symbolHelp.symbolDisplayType = 'Namespace';  
            }  
            if (e.completionItem.value._isEnum) {  
                e.symbolHelp.symbolDisplayType = 'Enum';  
            }  
        }  
    });  
    ```  
  
3. 加入下列參考指示詞，做為 appCode.js 的第一行。 這裡使用的路徑表示 JavaScript 檔案在同一個資料夾中。  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4. 在 appCode.js 中，輸入以下程式碼。 雖然您輸入時，您會看到 命名空間的圖示已變更為 「{}"，因為在 C# 中使用。  
  
     ![Glyph 屬性的使用範例](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")  
  
5. 在 appCode.js 中，輸入以下程式碼。 雖然您輸入時，您會看到新的列舉類型圖示 Enum1 成員和 SomeClass1 成員的新類別圖示。  
  
     ![Glyph 屬性的使用範例](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")  
  
### <a name="Overriding"></a> 避免執行階段影響 IntelliSense 結果  
 JavaScript 語言服務會執行程式碼，以動態方式提供 IntelliSense 資訊。 如此一來，執行階段行為可能偶爾會干擾想要的結果。 下列程序示範如何覆寫 IntelliSense 結果，當執行階段行為會導致不正確的 IntelliSense。  
  
 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:  
  
- exampleLib.js，是代表協力廠商程式庫的專案檔。  
  
- exampleLib.intellisense.js，是 IntelliSense 擴充功能。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。  
  
- 這個 appCode.js 是代表應用程式程式碼的專案檔。  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>若要避免執行階段影響 IntelliSense 結果  
  
1. 將下列程式碼新增至 exampleLib.js 中。  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     前面的程式碼包裝函式會忽略的值為基礎的初始呼叫`count`，也不會傳回結果。  
  
2. 加入下列參考指示詞，做為 appCode.js 的第一行。 這裡使用的路徑表示 JavaScript 檔案在同一個資料夾中。  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3. 在 appCode.js 中，輸入以下程式碼。 包裝函式永遠不會呼叫時，這表示因為識別項清單隨即出現而不是 IntelliSense`throttled`函式未傳回任何結果。  
  
     ![覆寫 intellisense 結果的範例](../ide/media/js-intellisense-override.png "js_intellisense_override")  
  
4. 將下列程式碼新增至 exampleLib.intellisense.js 中。 這會變更設計階段行為，讓 IntelliSense 會顯示為已包裝的函式，如預期般運作。  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5. 在 appCode.js 中，請輸入您先前輸入的相同程式碼測試結果。 此時，IntelliSense 會提供所需的資訊。  
  
     ![覆寫 IntelliSense 結果的範例](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [識別項的陳述式完成](../ide/statement-completion-for-identifiers.md)
