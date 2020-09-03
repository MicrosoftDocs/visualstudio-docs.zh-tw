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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665758"
---
# <a name="extending-javascript-intellisense"></a>擴充 JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript IntelliSense 擴充性功能可讓您在 JavaScript 編輯器中為協力廠商程式庫自訂 IntelliSense 結果。 這可以改善使用這些程式庫的開發人員體驗。

 JavaScript 語言服務會為新增至專案的協力廠商 JavaScript 程式庫提供 IntelliSense 功能。 針對大部分的程式庫，語言服務會自動提供語句完成。 下圖顯示語句完成的範例：

 ![陳述式完成範例](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 如果您的程式庫包含標準 JavaScript 註解標記中的變數、函式和物件的描述 (//) ，則根據預設，您會從 IntelliSense 擴充性功能中自動獲益，此擴充功能會在完成清單中專案右邊的快顯視窗中提供描述性資訊，或在函式呼叫中輸入左括弧。 彈出方塊中的批註包含成員的描述。 下列範例顯示完成清單的彈出方塊。

 ![快速資訊 pop&#45;up box 範例](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 若要進一步改善開發人員體驗，您可能會想要在快顯方塊中提供類型資訊給開發人員。 您可以使用 JavaScript [XML 檔批註](../ide/xml-documentation-comments-javascript.md) （而不是標準註解標記）來提供類型資訊。 您可以使用三個斜線註解標記（ (///) 和一組已定義的 XML 元素）來加入 XML 檔批註。

 或者，您也可以使用 JavaScript IntelliSense 擴充性來提供類型資訊。 這項功能可讓您建立 JavaScript 延伸模組並將其新增至腳本內容，以自訂 IntelliSense 結果。 在擴充功能（也就是 JavaScript 檔案）中，您會訂閱由語言服務的物件所公開的事件 `intellisense` 。 如果程式庫中的行為模式防止 JavaScript 語言服務提供所需的 IntelliSense 支援層級，而且也需要宣告式 XML 檔批註的替代方案，JavaScript IntelliSense 擴充性就是程式庫偏好的解決方案。 藉由自訂 IntelliSense 結果，您可以建立頂級 IntelliSense 體驗，而不論任何可能會限制語言服務預設功能的行為模式。 如需詳細資訊，請參閱[識別項的陳述式完成](../ide/statement-completion-for-identifiers.md)。

## <a name="adding-an-extension-to-the-script-context"></a>將延伸模組新增至腳本內容
 若要執行 IntelliSense 延伸模組，必須將它加入至目前的腳本內容。 自動探索機制可以自動將延伸加入至腳本內容，或者您也可以使用參考群組或參考指示詞，以手動方式將擴充功能加入至腳本內容。

 自動探索機制可讓語言服務自動尋找遵循檔案命名慣例 *>libraryname*.intellisense.js 的延伸模組，並將其放在與延伸模組套用的程式庫相同的目錄中。 例如，jQuery 程式庫的有效延伸模組將會 jQuery.intellisense.js。 針對更嚴格的 jQuery 擴充功能，您可以使用檔案名，例如 jQuery-1.7.1.intellisense.js (特定版本的副檔名) 或 jQuery.ui.intellisense.js (範圍 jQuery 程式庫) 的延伸模組。 如果找到指定程式庫的多個擴充功能，則會使用最嚴格的延伸模組版本。

 如果您想要將擴充功能用於所有 JavaScript 專案檔，您可以改為選擇將擴充功能加入至參考群組。 有數種類型的參考群組，也就是包含隱含參考的型別，以及包含專用背景工作參考的型別。 若要加入延伸模組，您通常需要將檔案新增為隱含的參考群組，也就是隱含的 ** (Windows) **、 **隱含 (Web) **。 隱含參考是在程式碼編輯器中開啟的每一個 .js 檔案範圍內。 當您使用這個方法時，您必須同時加入擴充功能和擴充功能所補充的檔案。

 您可以使用 [**選項**] 對話方塊的 [ **IntelliSense** ] 頁面，將延伸加入為參考群組。 您可以選擇功能表列上的 [**工具**]、[**選項**]，然後選擇 [**文字編輯器**]、[ **JavaScript**]、[ **IntelliSense**]、[**參考**]，來存取**IntelliSense**頁面。 如需參考群組的詳細資訊，請參閱 [JAVAscript intellisense](../ide/javascript-intellisense.md) 和 [選項、文字編輯器、javascript、IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md)。

 如果您想要將擴充功能用於一組特定的檔案，請使用參考指示詞。 當您使用這個方法時，您需要參考延伸模組和擴充功能所補充的檔案。 如需使用 reference 指示詞的詳細資訊，請參閱 [JavaScript IntelliSense](../ide/javascript-intellisense.md)。

## <a name="handling-intellisense-events"></a>處理 IntelliSense 事件
 擴充性功能可讓您藉由訂閱事件（例如 language service 物件的事件）來自訂 IntelliSense 結果 `statementcompletion` `intellisense` 。 下列範例顯示一個簡單的擴充功能，語言服務會使用此擴充功能來隱藏開頭為語句完成之底線的成員。 此程式碼包含在 underscorefilter.js 中，而且位於 \\ \\ *Visual Studio 安裝路徑*\JavaScript\References 資料夾中。

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

 在上述程式碼中，延伸模組會檢查事件物件的 [TargetName 屬性](#TargetName) 和 [目標屬性](#Target) 屬性， `statementcompletion` 以排除物件（例如 `this` 和 `window` ），並確保可以識別有效的語句完成清單。 如果可以識別完成清單，擴充功能就會篩選出以底線開頭的成員，藉以更新語句完成 [專案屬性](#Items) 集合。

 如需其他範例，請查看 \\ \\ *Visual Studio 安裝路徑*\JavaScript\References 資料夾。 此資料夾中的 showPlainComments.js 檔案會提供範例，說明如何使用其他事件來提供標準 JavaScript 註解標記的預設 IntelliSense 支援 (//) 。 如同 underscorefilter.js，showPlainComments.js 已可作為工作擴充功能使用，而且您可以在程式碼中針對變數、函式和物件使用註解標記時，看到產生的 IntelliSense 資訊。 如需其他範例，請參閱程式 [代碼範例](#CodeExamples)。

> [!WARNING]
> 如果您修改 Visual Studio 隨附的擴充檔案，您可以停用 JavaScript IntelliSense 或延伸模組所支援的功能。

 在您的延伸模組程式碼中，您可以使用下列專案來建立下列事件種類的處理常式 `addEventListener` ：

- `statementcompletion`，這會加入語句完成事件的處理常式。 當您輸入特殊字元（例如句號 (. ) ），或是當您輸入或按下 CTRL + J 時出現的識別碼清單，語句完成會提供特定類型的成員清單。處理常式會接收類型的事件物件 `CompletionEvent` ，此物件支援下列成員： [items 屬性](#Items)、 [Target property](#Target)、 [targetName 屬性](#TargetName)和 [scope 屬性](#Scope)。

- `signaturehelp`，這會加入 IntelliSense 參數資訊的處理常式。 參數資訊可提供函數所需參數數目、名稱和類型的相關資訊。 處理常式會接收類型的事件物件 `SignatureHelpEvent` ，此物件支援下列成員： [target 屬性](#Target)、 [ParentObject 屬性](#ParentObject)、 [functionComments 屬性](#FunctionComments)、 [functionHelp 屬性](#FunctionHelp)。

- `statementcompletionhint`，這會加入 IntelliSense 快速諮詢的處理常式。 [快速諮詢] 快顯方塊會顯示程式碼中識別碼的完整宣告。 處理常式會接收類型的事件物件 `CompletionHintEvent` ，此物件支援下列成員： [completionItem 屬性](#CompletionItem)和 [symbolHelp 屬性](#SymbolHelp)。

  如需顯示 IntelliSense 功能的範例，例如語句完成、參數資訊和快速諮詢，請參閱 [使用 intellisense](../ide/using-intellisense.md)。

> [!NOTE]
> 在 JavaScript 中，快速諮詢是指顯示在完成清單右邊的彈出方塊。 您無法手動叫用 [快速諮詢]。

## <a name="intellisense-object"></a><a name="intellisenseObject"></a> intellisense 物件
 下表顯示物件可使用的函數 `intellisense` 。 `intellisense`物件只能在設計階段使用。

|函式|說明|
|--------------|-----------------|
|`addEventListener(type, handler);`|加入 IntelliSense 事件的事件處理常式。<br /><br /> `type` 為字串值。 有效的值包括 `statementcompletion`、`signaturehelp` 和 `statementcompletionhint`。<br /><br /> `handler` 是一個事件處理常式函式，它會接收下列其中一種類型的事件物件：<br /><br /> -   `CompletionEvent`，用於 `statementcompletion` 事件。<br />-   `SignatureHelpEvent`，用於 `signaturehelp` 事件。<br />-   `CompletionHintEvent`，用於 `statementcompletionhint` 事件。<br /><br /> 如需使用此函數的範例，請參閱程式 [代碼範例](#CodeExamples)。|
|`annotate(obj, doc);`|藉由將檔批註從某個物件複製到另一個物件，指定物件的檔。<br /><br /> `obj` 指定要將檔案複製到其中的物件。<br /><br /> `doc` 指定要從中複製檔的物件。<br /><br /> 如需示範如何使用此函式的範例，請參閱 [加入 IntelliSense 批註](#Annotations)。|
|`getFunctionComments(func);`|傳回指定之函數的批註。<br /><br /> `func` 指定要傳回其批註的函式。<br /><br /> 您可以使用來設定 `func` 參數 `completionItem.value` 。<br /><br /> 傳回的 `functionComments` 物件包含下列成員： `above` 、 `inside` 和 `paramComment` 。 如需詳細資訊，請參閱 [FunctionComments 屬性](#FunctionComments) 屬性。<br /><br /> `getFunctionComments` 只能從所註冊的其中一個事件處理常式中呼叫 `addEventListener` 。<br /><br /> 如需顯示如何使用此函式的範例，請參閱 \\ \\ *Visual Studio 安裝路徑*\JavaScript\References\showPlainComments.js。|
|`logMessage(msg);`|將診斷訊息傳送至 [輸出] 視窗。<br /><br /> `msg` 這是包含訊息的字串。<br /><br /> 如需示範如何使用此函式的範例，請參閱將 [訊息傳送至輸出視窗](#Logging)。|
|`nullWithCompletionsOf(value);`|傳回特殊的 null 值，此值是由參數中傳遞的物件所決定的完成清單 `value` 。<br /><br /> `value` 判斷傳回值的完成清單。 `value` 可以是任何類型。<br /><br /> 在設計階段會將 null 傳回值視為 null，但傳回值的完成清單與參數的完成清單相同 `value` 。<br /><br /> 這項功能的其中一個用途是在執行時間可預測傳回型別時，提供傳回值的 IntelliSense，但是在設計階段則傳回值 `null` 。|
|`redirectDefinition(func, definition);`|當要求參數說明或 **移至定義** 時，指示 IntelliSense 使用提供的定義函式，而不是原始的 func 函數。<br /><br /> `func` 指定目標函數。<br /><br /> `definition` 指定要使用的函式，而不是參數資訊的目標函式和 [ **移至定義**]。|
|`setCallContext(func, thisArg);`|設定指定之函式的呼叫內容（或範圍）。<br /><br /> `func` 指定要設定範圍的函式。<br /><br /> `thisArg` 這是關鍵字可參考的物件常值 `this` ，可指定成員的新範圍。 您可以包含要傳入此參數的引數，例如 `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` 提供類似的行為 `Function.prototype.bind` ，不同之處在于它僅用於設計階段的 IntelliSense 支援。 `setCallContext`如果您需要模擬無法存取的程式碼呼叫，您可以使用來設定函式範圍，如此一來，當您呼叫函式時，函式呼叫就會包含正確的範圍和引數。|
|`undefinedWithCompletionsOf(value);`|傳回特殊的未定義值，其完成清單是由參數中傳遞的物件所決定 `value` 。<br /><br /> `value` 判斷傳回值的完成清單。 `value` 可以是任何類型。<br /><br /> 未定義的傳回值會在設計階段被視為未定義，但傳回值的完成清單與參數的完成清單相同 `value` 。<br /><br /> 這項功能的其中一個用途是在執行時間可預測傳回型別時，提供傳回值的 IntelliSense，但是在設計階段時，傳回值是未定義的。|
|`version()`|傳回 Visual Studio 版本。|

## <a name="event-members"></a>事件成員
 下列各節描述在事件物件中公開給下列事件的成員： `statementcompletion` 、 `signaturehelp` 和 `statementcompletionhint` 。

### <a name="completionitem-property"></a><a name="CompletionItem"></a> completionItem 屬性
 傳回要求快速諮詢快顯方塊的識別碼，稱為完成專案。 這個屬性可供 `statementcompletionhint` 事件物件和事件物件的 [items 屬性](#Items) 屬性使用 `statementcompletion` 。

 傳回值： `completionItem` 物件

 以下是物件的成員 `completionItem` ：

- `name`. 在集合中使用時讀取/寫入 `items` ，否則為唯讀。 傳回識別完成專案的字串。

- `kind`. 在集合中使用時讀取/寫入 `items` ，否則為唯讀。 傳回表示完成專案類型的字串。 可能的值為方法、欄位、屬性、參數、變數和保留。

- `glyph`. 在集合中使用時讀取/寫入 `items` ，否則為唯讀。 傳回字串，表示顯示在完成清單中的圖示。 的可能值 `glyph` 使用下列格式： vs：*glyphType*，其中 *glyphType* 對應至列舉中的語言獨立成員 <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> 。 例如， `vs:GlyphGroupMethod` 是的一個可能值 `glyph` 。 當 `glyph` 未設定時， `kind` 屬性會決定預設圖示。

- `parentObject`. 唯讀。 傳回父物件。

- `value`. 唯讀。 傳回物件，表示完成專案的值。

- `comments`. 唯讀。 傳回包含欄位或變數上方批註的字串。

- `scope`. 唯讀。 傳回完成專案的範圍。 可能的值為 global、local、parameter 和 member。

### <a name="items-property"></a><a name="Items"></a> items 屬性
 取得或設定語句完成專案的陣列。 陣列中的每個元素都是 [CompletionItem 屬性](#CompletionItem) 物件。 `items`屬性可用於 `statementcompletion` 事件物件。

 傳回值：陣列

### <a name="functioncomments-property"></a><a name="FunctionComments"></a> functionComments 屬性
 傳回函數的批註。 這個屬性可用於 `signaturehelp` 事件物件。

 傳回值： `comments` 物件

 以下是物件的成員 `comments` ：

- `above`. 傳回函數上方的批註。

- `inside`. 傳回函數內部的批註，通常是 VSDoc 格式。

- `paramComments`. 傳回陣列，表示函數中每個參數的批註。 陣列的成員包括：

  - `name`. 傳回代表參數名稱的字串。

  - `comment`. 傳回包含參數批註的字串。

### <a name="functionhelp-property"></a><a name="FunctionHelp"></a> functionHelp 屬性
 傳回函數的說明。 這個屬性可用於 `signaturehelp` 事件物件。

 傳回值： `functionHelp` 物件

 以下是物件的成員 `functionHelp` ：

- `functionName`. 讀取/寫入 傳回包含函式名稱的字串。

- `signatures`. 讀取/寫入 取得或設定函式特徵標記的陣列。 陣列中的每個元素都是 `signature` 物件。 某些 `signature` 屬性（例如 `locid` ）會對應至一般 [XML 檔批註](../ide/xml-documentation-comments-javascript.md) 屬性。

  物件的成員 `signature` 包括：

  - `description`. 讀取/寫入 傳回描述函數的字串。

  - `locid`. 讀取/寫入 傳回包含函數之當地語系化資訊的字串識別碼。

  - `helpKeyword`. 讀取/寫入 傳回包含 Help 關鍵字的字串。

  - `externalFile`. 讀取/寫入 傳回字串，表示包含成員識別碼的檔案。

  - `externalid`. 讀取/寫入 傳回表示函數成員識別碼的字串。

  - `params`. 讀取/寫入 取得或設定函數的參數陣列。 Parameters 陣列中的每個專案都是一個 `parameter` 物件，該物件的屬性會對應至元素的下列屬性 [\<param>](../ide/param-javascript.md) ：

    - `name`. 讀取/寫入 傳回代表參數名稱的字串。

    - `type`. 讀取/寫入 傳回表示參數類型的字串。

    - `elementType`. 讀取/寫入 如果類型為，則會傳回 `Array` 字串，表示陣列中的元素類型。

    - `description`. 讀取/寫入 傳回描述參數的字串。

    - `locid`. 讀取/寫入 傳回包含函數之當地語系化資訊的字串識別碼。

    - `optional`. 讀取/寫入 傳回字串，這個字串表示參數是否為選擇性。 `true` 表示參數為選擇性。 `false` 指出它不是。

  - `returnValue`. 讀取/寫入 取得或設定傳回值物件，其屬性會對應到元素的下列屬性 [\<returns>](../ide/returns-javascript.md) ：

    - `type`. 讀取/寫入 傳回表示傳回型別的字串。

    - `elementType`. 讀取/寫入 如果類型為，則會傳回 `Array` 字串，表示陣列中的元素類型。

    - `description`. 讀取/寫入 傳回描述傳回值的字串。

    - `locid`. 讀取/寫入 傳回包含函數之當地語系化資訊的字串識別碼。

    - `helpKeyword`. 讀取/寫入 傳回包含 Help 關鍵字的字串。

    - `externalFile`. 讀取/寫入 傳回字串，表示包含成員識別碼的檔案。

    - `externalid`. 讀取/寫入 傳回表示函數成員識別碼的字串。

### <a name="parentobject-property"></a><a name="ParentObject"></a> parentObject 屬性
 傳回成員函式的父物件。 例如，若是 `document.getElementByID` ，則會傳回 `parentObject` `document` 物件。 這個屬性可用於 `signaturehelp` 事件物件。

 傳回值：物件

### <a name="target-property"></a><a name="Target"></a> 目標屬性
 傳回物件，這個物件表示觸發程式字元左邊的專案，這是 ( 的句點。 ) 。 針對函式，傳回 `target` 要求參數資訊的函式。 這個屬性適用于 `statementcompletion` 和 `signaturehelp` 事件物件。

 傳回值：物件

### <a name="targetname-property"></a><a name="TargetName"></a> targetName 屬性
 傳回表示目標的字串。 例如，針對 "this."，會傳回 `targetName` "this"。 若為 "A. B" (當游標在 "B" ) 之後，會傳回 `targetName` "b"。 這個屬性可用於 `statementcompletion` 事件物件。

 傳回值：字串

### <a name="symbolhelp-property"></a><a name="SymbolHelp"></a> symbolHelp 屬性
 傳回已要求快速諮詢彈出方塊的完成專案。 這個屬性可用於 `statementcompletionhint` 事件物件。

 傳回值： `symbolHelp` object。

 物件的某些屬性（ `symbolHelp` 例如）會 `locid` 對應至一般 [XML 檔批註](../ide/xml-documentation-comments-javascript.md) 屬性。

 以下是物件的成員 `symbolHelp` ：

- `name`. 讀取/寫入 傳回包含識別碼名稱的字串。

- `symbolType`. 讀取/寫入 傳回表示符號類型的字串。 可能的值包括未知、布林值、數位、字串、物件、函數、陣列、日期和 Regex。

- `symbolDisplayType`. 讀取/寫入 傳回字串，其中包含要顯示的型別名稱。 如果 `symbolDisplayType` 未設定， `symbolType` 則會使用。

- `elementType`. 讀取/寫入 如果 `symbolType` 是，則會傳回 `Array` 字串，表示陣列中專案的類型。

- `scope`. 讀取/寫入 傳回表示符號範圍的字串。 可能的值包括 global、local、parameter 和 member。

- `description`. 讀取/寫入 傳回字串，其中包含符號的描述。

- `locid`. 讀取/寫入 傳回包含符號之當地語系化資訊的字串識別碼。

- `helpKeyword`. 讀取/寫入 傳回包含 Help 關鍵字的字串。

- `externalFile`. 讀取/寫入 傳回字串，表示包含成員識別碼的檔案。

- `externalid`. 讀取/寫入 傳回字串，表示符號的成員識別碼。

- `functionHelp`. 讀取/寫入 傳回 [FunctionHelp 屬性](#FunctionHelp)，此屬性可能會在為函式時包含資訊 `symbolType` 。

### <a name="scope-property"></a><a name="Scope"></a> scope 屬性
 傳回事件的完成範圍。 完成範圍的可能值為全域和成員。 這個屬性可用於 `statementcompletion` 事件物件。

 傳回值：字串

## <a name="debugging-intellisense-extensions"></a>IntelliSense 擴充功能的調試
 您無法 debug 擴充功能，但您可以使用 [Intellisense 物件](#intellisenseObject) 函數將資訊傳送至 Visual Studio 的輸出視窗。 如需示範如何使用此函式的範例，請參閱本主題稍後的將 [訊息傳送至輸出視窗](#Logging) 。 `logMessage`若要運作，至少必須在擴充中註冊一個事件處理常式。

## <a name="code-examples"></a><a name="CodeExamples"></a> 程式碼範例
 本節包含示範如何使用 IntelliSense 擴充性 Api 的程式碼範例。 另外還有其他使用這些 Api 的方式。 如需其他範例，請參閱 \\ \\ *Visual Studio 安裝路徑*\JavaScript\References 資料夾中的下列檔案。 這些是 JavaScript 語言服務所使用的實用範例。

- underscoreFilter.js。 此程式碼會從 IntelliSense 隱藏私用成員。 它包含事件的事件處理常式 `statementcompletion` 。

- showPlainComments.js。 這段程式碼會為標準批註提供 IntelliSense 支援。 它包含和事件的事件處理常式 `signaturehelp` `statementcompletionhint` 。

### <a name="adding-intellisense-annotations"></a><a name="Annotations"></a> 加入 IntelliSense 注釋
 下列程式顯示如何為協力廠商程式庫提供 IntelliSense 檔支援，而不需要直接修改程式庫。 若要這樣做，您可以 `intellisense.annotate` 在延伸模組中使用。

 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:

- demoLib.js，這是代表協力廠商程式庫的專案檔。

- demoLib.intellisense.js，也就是 IntelliSense 延伸模組。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。

- 這個 appCode.js 是代表應用程式程式碼的專案檔。

##### <a name="to-add-an-intellisense-annotation"></a>加入 IntelliSense 注釋

1. 將下列程式碼新增至 demoLib.js。

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. 將下列程式碼新增至 demoLib.intellisense.js。

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

4. 在 appCode.js 中，輸入以下程式碼。 您會在擴充功能中看到顯示為 IntelliSense 參數資訊的 XML 檔批註。

     ![intellisense.annotate 的使用範例](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. 在 appCode.js 中，輸入以下程式碼。 當您輸入時，會看到延伸模組中的標準批註顯示為 IntelliSense 快速諮詢。

     ![intellisense.annotate 的使用範例](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="sending-messages-to-the-output-window"></a><a name="Logging"></a> 將訊息傳送至輸出視窗
 下列程式顯示如何將訊息傳送至 [輸出] 視窗。 您可以傳送訊息來協助調試 IntelliSense 延伸模組。

 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:

- exampleLib.js，這是代表協力廠商程式庫的專案檔。

- exampleLib.intellisense.js，也就是 IntelliSense 延伸模組。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。

- 這個 appCode.js 是代表應用程式程式碼的專案檔。

##### <a name="to-send-a-message-to-the-output-window"></a>將訊息傳送至輸出視窗

1. 將下列程式碼新增至 exampleLib.js。

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. 將下列程式碼新增至 exampleLib.intellisense.js。

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

4. 在 [輸出] 視窗中，選擇 [**顯示輸出來源**] 清單中的 [ **JavaScript Language Service** ]。  (若要查看 [輸出] 視窗，請從 [View] 功能表選取 [ **輸出** ]。 ) 

5. 在 appCode.js 中，輸入以下程式碼。 當您輸入時，[輸出] 視窗會顯示來自語言服務的訊息。 [輸出] 視窗中的第一則訊息表示已要求目前範圍的語句完成。

    ```javascript
    some
    ```

     以下是您應該會看到的輸出的部分觀點。

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. 選擇 [輸出] 視窗中的 [ **全部清除** ] 按鈕。

7. 輸入下列程式碼。 [輸出] 視窗中的第一則訊息，指出已要求成員清單。

    ```javascript
    someVar.
    ```

     以下是您應該會看到的輸出的部分觀點：

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="changing-the-intellisense-icons"></a><a name="Icons"></a> 變更 IntelliSense 圖示
 下列程式顯示如何變更 IntelliSense 預設顯示的圖示。 當您提供有關程式庫特定概念的 IntelliSense 資訊（例如命名空間、類別、介面和列舉）時，這可能會很有用。

 如需可用的圖示值，請參閱 <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> 。

 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:

- exampleLib.js，這是 represens 協力廠商程式庫的專案檔。

- exampleLib.intellisense.js，也就是 IntelliSense 延伸模組。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。

- 這個 appCode.js 是代表應用程式程式碼的專案檔。

##### <a name="to-change-the-icons"></a>變更圖示

1. 將下列程式碼新增至 exampleLib.js。

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

2. 將下列程式碼新增至 exampleLib.intellisense.js。

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

4. 在 appCode.js 中，輸入以下程式碼。 當您輸入時，您會看到命名空間的圖示已變更為 " {} "，如同 c # 中所使用。

     ![glyph 屬性的使用範例](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. 在 appCode.js 中，輸入以下程式碼。 當您輸入時，您會看到 Enum1 成員的新列舉圖示，以及 SomeClass1 成員的新類別圖示。

     ![glyph 屬性的使用範例](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="avoiding-run-time-effects-on-intellisense-results"></a><a name="Overriding"></a> 避免對 IntelliSense 結果產生執行時間效果
 JavaScript 語言服務會執行程式碼，以動態方式提供 IntelliSense 資訊。 因此，執行時間行為偶爾會干擾所需的結果。 下列程式顯示如何在執行時間行為導致不正確的 IntelliSense 時，覆寫 IntelliSense 結果。

 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:

- exampleLib.js，這是代表協力廠商程式庫的專案檔。

- exampleLib.intellisense.js，也就是 IntelliSense 延伸模組。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。

- 這個 appCode.js 是代表應用程式程式碼的專案檔。

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>若要避免執行時間對 IntelliSense 結果的影響

1. 將下列程式碼新增至 exampleLib.js。

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     在上述程式碼中，包裝的函式會根據的值忽略初始呼叫， `count` 而不會傳回結果。

2. 加入下列參考指示詞，做為 appCode.js 的第一行。 這裡使用的路徑表示 JavaScript 檔案在同一個資料夾中。

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. 在 appCode.js 中，輸入以下程式碼。 識別碼清單會出現，而非 IntelliSense，因為永遠不會呼叫包裝的函式，這表示函式不會傳回 `throttled` 任何結果。

     ![覆寫 intellisense 結果的範例](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. 將下列程式碼新增至 exampleLib.intellisense.js。 這會變更設計階段行為，如此就能如預期般顯示已包裝函式的 IntelliSense。

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. 在 appCode.js 中，輸入您先前輸入的相同程式碼來測試結果。 這次，IntelliSense 會提供所需的資訊。

     ![覆寫 IntelliSense 結果的範例](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>另請參閱
 識別碼的[JavaScript IntelliSense](../ide/javascript-intellisense.md) [語句完成](../ide/statement-completion-for-identifiers.md)
