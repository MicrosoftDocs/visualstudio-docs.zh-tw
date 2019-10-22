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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665758"
---
# <a name="extending-javascript-intellisense"></a>擴充 JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript IntelliSense 擴充性功能可讓您針對協力廠商程式庫，自訂 JavaScript 編輯器中的 IntelliSense 結果。 這可以改善使用這些程式庫的開發人員體驗。

 JavaScript 語言服務會針對新增至專案的協力廠商 JavaScript 程式庫提供 IntelliSense 功能。 對於大部分的程式庫而言，語言服務會自動提供語句完成。 下圖顯示語句完成的範例：

 ![語句完成的範例](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 如果您的程式庫在標準 JavaScript 註解標記（//）中包含變數、函式和物件的描述，則根據預設，您會從 IntelliSense 擴充性功能自動受益，而在彈出方塊中提供描述性資訊出現在完成清單中的元素右邊，或當您在函式呼叫中輸入左括弧時。 快顯方塊中的批註包含成員的描述。 下列範例顯示完成清單的快顯方塊。

 ![[快速諮詢] 快&#45;顯方塊的範例](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 若要進一步改善開發人員體驗，您可能會想要在快顯方塊中提供類型資訊給開發人員。 您可以使用 JavaScript [XML 檔批註](../ide/xml-documentation-comments-javascript.md)，而不是標準註解標記來提供類型資訊。 您可以使用三斜線註解標記（///）和一組已定義的 XML 專案來加入 XML 檔批註。

 或者，您可以使用 JavaScript IntelliSense 擴充性來提供類型資訊。 這項功能可讓您建立 JavaScript 延伸模組並將其加入至腳本內容，以自訂 IntelliSense 結果。 在擴充功能（也就是 JavaScript 檔案）中，您訂閱了語言服務的 `intellisense` 物件所公開的事件。 如果程式庫中的行為模式防止 JavaScript 語言服務提供所需的 IntelliSense 支援層級，以及宣告式 XML 的替代方法，JavaScript IntelliSense 擴充性就是程式庫的慣用解決方案也需要檔批註。 藉由自訂 IntelliSense 結果，您可以建立最先進的 IntelliSense 體驗，而不論可能限制語言服務預設功能的任何行為模式。 如需詳細資訊，請參閱[識別項的陳述式完成](../ide/statement-completion-for-identifiers.md)。

## <a name="adding-an-extension-to-the-script-context"></a>將延伸模組加入至腳本內容
 針對要執行的 IntelliSense 延伸模組，必須將它加入至目前的腳本內容。 延伸模組可以透過自動探索機制自動加入至腳本內容，或者您可以使用參考群組或 reference 指示詞，以手動方式將擴充功能加入至腳本內容。

 自動探索機制可讓語言服務自動尋找遵循檔案命名慣例*libraryname*的延伸模組，並將其放在與擴充功能的程式庫相同的目錄中。適用于. 例如，jQuery 程式庫的有效延伸模組會是 jQuery. intellisense .js。 如需更嚴格的 jQuery 擴充功能，您可以使用檔案名（例如 Jquery-1.7.2.min.js 1.7.1）或 jQuery. node.js （範圍 jQuery 程式庫的延伸模組）。 如果找到指定程式庫的多個延伸模組，則會使用最嚴格的延伸模組版本。

 如果您想要對所有 JavaScript 專案檔使用此延伸模組，您可以改為選擇將擴充功能加入至參考群組。 有數種類型的參考群組，其中包括隱含參考和包含專用背景工作參考的型別。 若要加入擴充功能，您通常需要將檔案新增為隱含的參考群組，也就是**隱含（Windows）** 、**隱含（Web）** 。 隱含參考會在程式碼編輯器中開啟的每個 .js 檔案範圍內。 當您使用這個方法時，您需要同時新增延伸模組和擴充功能所補充的檔案。

 使用 [**選項**] 對話方塊的 [ **IntelliSense** ] 頁面，即可加入擴充做為參考群組。 您可以透過選擇功能表列上的 **[工具**]、[**選項**]，然後選擇 [**文字編輯器**]、[ **JavaScript**]、[ **IntelliSense**]、[**參考**]，來存取**IntelliSense**頁面。 如需參考群組的詳細資訊，請參閱[JAVAscript IntelliSense](../ide/javascript-intellisense.md)和[選項、文字編輯器、javascript、IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md)。

 如果您想要針對一組特定的檔案使用此延伸模組，請使用 reference 指示詞。 當您使用這個方法時，您必須同時參考延伸模組和副檔名所補充的檔案。 如需使用 reference 指示詞的詳細資訊，請參閱[JavaScript IntelliSense](../ide/javascript-intellisense.md)。

## <a name="handling-intellisense-events"></a>處理 IntelliSense 事件
 擴充性功能可讓您藉由訂閱事件（例如語言服務 `intellisense` 物件的 `statementcompletion` 事件）來自訂 IntelliSense 結果。 下列範例顯示語言服務用來隱藏語句完成後以底線開頭之成員的簡單延伸模組。 這段程式碼包含在 underscorefilter 中，而且位於 \\ \\*Visual Studio 安裝路徑*\JavaScript\References 資料夾中。

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

 在上述程式碼中，延伸模組會檢查 `statementcompletion` 事件物件的[TargetName 屬性](#TargetName)和[目標屬性](#Target)屬性，以排除物件（例如 `this` 和 `window`），並確保有效的語句完成清單可以是認定. 如果可以識別完成清單，延伸模組會藉由篩選出以底線開頭的成員，來更新語句完成[專案屬性](#Items)集合。

 如需其他範例，請查看 \\ \\*Visual Studio 安裝路徑*\JavaScript\References 資料夾。 此資料夾中的 showPlainComments 會提供一些範例，說明如何使用其他事件來提供標準 JavaScript 註解標記（//）的預設 IntelliSense 支援。 如同 underscorefilter，showPlainComments 已經可做為工作延伸模組，當您在程式碼中針對變數、函式和物件使用註解標記時，您可以看到所產生的 IntelliSense 資訊。 如需其他範例，請參閱程式[代碼範例](#CodeExamples)。

> [!WARNING]
> 如果您修改 Visual Studio 隨附的延伸模組檔案，可能會停用 JavaScript IntelliSense 或擴充功能所支援的功能。

 在您的擴充程式碼中，您可以使用 `addEventListener` 來建立下列事件種類的處理常式：

- `statementcompletion`，它會加入語句完成事件的處理常式。 語句完成提供特定類型的成員清單，當您輸入特殊字元（例如句號（.）），或是當您輸入或按下 CTRL + J 時出現的識別碼清單時，就會出現此清單。處理常式會接收 `CompletionEvent` 類型的事件物件，其支援下列成員： [Items 屬性](#Items)、 [target 屬性](#Target)、 [targetName 屬性](#TargetName)和[scope 屬性](#Scope)。

- `signaturehelp`，它會加入 IntelliSense 參數資訊的處理常式。 參數資訊提供函式所需之參數數目、名稱和類型的相關資訊。 處理常式會接收 `SignatureHelpEvent` 類型的事件物件，其支援下列成員： [Target 屬性](#Target)、 [parentObject 屬性](#ParentObject)、 [functionComments 屬性](#FunctionComments)、 [functionHelp 屬性](#FunctionHelp)。

- `statementcompletionhint`，它會加入 IntelliSense 快速諮詢的處理常式。 [快速諮詢] 快顯方塊會顯示程式碼中識別碼的完整宣告。 處理常式會接收 `CompletionHintEvent` 類型的事件物件，其支援下列成員： [CompletionItem 屬性](#CompletionItem)和[symbolHelp 屬性](#SymbolHelp)。

  如需顯示 IntelliSense 功能（例如語句完成、參數資訊和快速諮詢）的範例，請參閱[使用 intellisense](../ide/using-intellisense.md)。

> [!NOTE]
> 在 JavaScript 中，[快速諮詢] 是指出現在完成清單右邊的快顯方塊。 您無法手動叫用 [快速諮詢]。

## <a name="intellisenseObject"></a> intellisense 物件
 下表顯示可用於 `intellisense` 物件的函數。 只有在設計階段才可使用 `intellisense` 物件。

|功能|描述|
|--------------|-----------------|
|`addEventListener(type, handler);`|加入 IntelliSense 事件的事件處理常式。<br /><br /> `type` 是字串值。 有效值包括 `statementcompletion`、`signaturehelp` 和 `statementcompletionhint`。<br /><br /> `handler` 是事件處理常式函式，它會接收下列其中一種類型的事件物件：<br /><br /> -    `CompletionEvent`，用於 `statementcompletion` 事件。<br />-    `SignatureHelpEvent`，用於 `signaturehelp` 事件。<br />-    `CompletionHintEvent`，用於 `statementcompletionhint` 事件。<br /><br /> 如需使用此函式的範例，請參閱程式[代碼範例](#CodeExamples)。|
|`annotate(obj, doc);`|藉由將檔批註從一個物件複製到另一個物件，指定物件的檔。<br /><br /> `obj` 指定要將檔案複製到其中的物件。<br /><br /> `doc` 指定要從中複製檔的物件。<br /><br /> 如需顯示如何使用此函式的範例，請參閱[加入 IntelliSense 注釋](#Annotations)。|
|`getFunctionComments(func);`|傳回指定之函式的批註。<br /><br /> `func` 指定要傳回批註的函式。<br /><br /> 您可以使用 `completionItem.value` 來設定 `func` 參數。<br /><br /> 傳回的 `functionComments` 物件包含下列成員： `above`、`inside` 和 `paramComment`。 如需詳細資訊，請參閱[FunctionComments 屬性](#FunctionComments)屬性。<br /><br /> `getFunctionComments` 只能從 `addEventListener` 所註冊的其中一個事件處理常式中呼叫。<br /><br /> 如需顯示如何使用此函式的範例，請參閱 \\ \\*Visual Studio 安裝路徑*\JavaScript\References\showPlainComments.js。|
|`logMessage(msg);`|將診斷訊息傳送至 [輸出] 視窗。<br /><br /> `msg` 是包含訊息的字串。<br /><br /> 如需顯示如何使用此函式的範例，請參閱將[訊息傳送至輸出視窗](#Logging)。|
|`nullWithCompletionsOf(value);`|傳回特殊的 null 值，完成清單是由 `value` 參數中傳遞的物件所決定。<br /><br /> `value` 決定傳回值的完成清單。 `value` 可以是任何類型。<br /><br /> Null 傳回值會在設計階段視為 null，但傳回值的完成清單會與 `value` 參數的完成清單相同。<br /><br /> 此函式的其中一種用途是在執行時間可預測傳回型別時，提供傳回值的 IntelliSense，但傳回值會在設計階段 `null`。|
|`redirectDefinition(func, definition);`|當要求參數 [說明] 或 [**移至定義**] 時，指示 IntelliSense 使用提供的定義函式，而不是原始的 func 函數。<br /><br /> `func` 指定目標函數。<br /><br /> `definition` 指定要使用的函式，而不是參數資訊的目標函式和 [**移至定義**]。|
|`setCallContext(func, thisArg);`|為指定的函式設定呼叫內容或範圍。<br /><br /> `func` 指定要設定範圍的函式。<br /><br /> `thisArg` 是 `this` 關鍵字可以參考的物件常值，它會指定成員的新範圍。 您可以包含要傳入此參數的引數，例如，`intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` 提供類似于 `Function.prototype.bind` 的行為，不同之處在于它只用于設計階段 IntelliSense 支援。 如果您需要模擬無法以其他方式存取的程式碼呼叫，您可以使用 `setCallContext` 設定函式範圍，如此一來，當您呼叫函式時，函式呼叫將會包含正確的範圍和引數。|
|`undefinedWithCompletionsOf(value);`|傳回特殊的未定義值，完成清單是由 `value` 參數中傳遞的物件所決定。<br /><br /> `value` 決定傳回值的完成清單。 `value` 可以是任何類型。<br /><br /> 未定義的傳回值會在設計階段被視為未定義，但傳回值的完成清單與 `value` 參數的完成清單相同。<br /><br /> 此函式的其中一個用途是在執行時間可預測傳回型別時，提供傳回值的 IntelliSense，但是在設計階段未定義傳回值。|
|`version()`|傳回 Visual Studio 版本。|

## <a name="event-members"></a>事件成員
 下列各節描述在事件物件中針對下列事件公開的成員： `statementcompletion`、`signaturehelp` 和 `statementcompletionhint`。

### <a name="CompletionItem"></a>completionItem 屬性
 傳回要求 [快速諮詢] 快顯方塊的識別碼，稱為完成專案。 這個屬性適用于 `statementcompletionhint` 事件物件，以及 `statementcompletion` 事件物件的[Items 屬性](#Items)屬性。

 傳回值： `completionItem` 物件

 以下是 `completionItem` 物件的成員：

- `name` 在 `items` 集合中使用時的讀取/寫入;否則為唯讀。 傳回識別完成專案的字串。

- `kind` 在 `items` 集合中使用時的讀取/寫入;否則為唯讀。 傳回表示完成專案類型的字串。 可能的值包括 method、field、property、parameter、variable 和 reserved。

- `glyph` 在 `items` 集合中使用時的讀取/寫入;否則為唯讀。 傳回字串，表示在完成清單中顯示的圖示。 @No__t_0 的可能值使用下列格式： vs：*glyphType*，其中*glyphType*對應至 <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> 列舉中與語言無關的成員。 例如，`vs:GlyphGroupMethod` 是 `glyph` 的一個可能值。 未設定 `glyph` 時，`kind` 屬性會決定預設圖示。

- `parentObject` 唯讀。 傳回父物件。

- `value` 唯讀。 傳回物件，表示完成專案的值。

- `comments` 唯讀。 傳回字串，其中包含欄位或變數上方的批註。

- `scope` 唯讀。 傳回完成專案的範圍。 可能的值為全域、本機、參數和成員。

### <a name="Items"></a>items 屬性
 取得或設定語句完成專案的陣列。 陣列中的每個元素都是[CompletionItem 屬性](#CompletionItem)物件。 @No__t_0 屬性可供 `statementcompletion` 事件物件使用。

 傳回值：陣列

### <a name="FunctionComments"></a>functionComments 屬性
 傳回函數的批註。 這個屬性可用於 `signaturehelp` 事件物件。

 傳回值： `comments` 物件

 以下是 `comments` 物件的成員：

- `above` 傳回函數上方的批註。

- `inside` 傳回函式內部的批註，通常採用 VSDoc 格式。

- `paramComments` 傳回陣列，表示函數中每個參數的批註。 陣列的成員包括：

  - `name` 傳回代表參數名稱的字串。

  - `comment` 傳回包含參數批註的字串。

### <a name="FunctionHelp"></a>functionHelp 屬性
 傳回函數的說明。 這個屬性可用於 `signaturehelp` 事件物件。

 傳回值： `functionHelp` 物件

 以下是 `functionHelp` 物件的成員：

- `functionName` 讀取/寫入。 傳回包含函數名稱的字串。

- `signatures` 讀取/寫入。 取得或設定函式簽章的陣列。 陣列中的每個元素都是 `signature` 物件。 某些 `signature` 屬性（例如 `locid`）會對應至一般[XML 檔批註](../ide/xml-documentation-comments-javascript.md)屬性。

  @No__t_0 物件的成員包括：

  - `description` 讀取/寫入。 傳回描述函數的字串。

  - `locid` 讀取/寫入。 傳回字串識別碼，其中包含有關函數的當地語系化資訊。

  - `helpKeyword` 讀取/寫入。 傳回包含 Help 關鍵字的字串。

  - `externalFile` 讀取/寫入。 傳回表示包含成員識別碼之檔案的字串。

  - `externalid` 讀取/寫入。 傳回表示函式成員識別碼的字串。

  - `params` 讀取/寫入。 取得或設定函數的參數陣列。 Parameters 陣列中的每個專案都是一個 `parameter` 物件，其屬性會對應至[\<param >](../ide/param-javascript.md)專案的下列屬性：

    - `name` 讀取/寫入。 傳回表示參數名稱的字串。

    - `type` 讀取/寫入。 傳回表示參數類型的字串。

    - `elementType` 讀取/寫入。 如果類型是 `Array`，會傳回代表陣列中元素類型的字串。

    - `description` 讀取/寫入。 傳回描述參數的字串。

    - `locid` 讀取/寫入。 傳回字串識別碼，其中包含有關函數的當地語系化資訊。

    - `optional` 讀取/寫入。 傳回表示參數是否為選擇性的字串。 `true` 表示參數是選擇性的; `false` 表示它不是。

  - `returnValue` 讀取/寫入。 取得或設定傳回值物件，其屬性會對應至[\<returns >](../ide/returns-javascript.md)元素的下列屬性：

    - `type` 讀取/寫入。 傳回表示傳回類型的字串。

    - `elementType` 讀取/寫入。 如果類型是 `Array`，會傳回代表陣列中元素類型的字串。

    - `description` 讀取/寫入。 傳回描述傳回值的字串。

    - `locid` 讀取/寫入。 傳回字串識別碼，其中包含有關函數的當地語系化資訊。

    - `helpKeyword` 讀取/寫入。 傳回包含 Help 關鍵字的字串。

    - `externalFile` 讀取/寫入。 傳回表示包含成員識別碼之檔案的字串。

    - `externalid` 讀取/寫入。 傳回表示函式成員識別碼的字串。

### <a name="ParentObject"></a>parentObject 屬性
 傳回成員函式的父物件。 例如，針對 `document.getElementByID`，`parentObject` 會傳回 `document` 物件。 這個屬性可用於 `signaturehelp` 事件物件。

 傳回值：物件

### <a name="Target"></a> 目標屬性
 傳回物件，代表觸發程式字元左邊的專案，也就是句點（.）。 針對函式，`target` 會傳回要求參數資訊的函式。 這個屬性適用于 `statementcompletion` 和 `signaturehelp` 事件物件。

 傳回值：物件

### <a name="TargetName"></a>targetName 屬性
 傳回表示目標的字串。 例如，對於 "this."，`targetName` 會傳回 "this"。 若為 "A. B" （當游標位於 "B" 之後）時，`targetName` 會傳回 "B"。 這個屬性可用於 `statementcompletion` 事件物件。

 傳回值：字串

### <a name="SymbolHelp"></a>symbolHelp 屬性
 傳回要求 [快速諮詢] 快顯方塊的完成專案。 這個屬性可用於 `statementcompletionhint` 事件物件。

 傳回值： `symbolHelp` 物件。

 @No__t_0 物件的某些屬性（例如 `locid`）會對應到一般[XML 檔批註](../ide/xml-documentation-comments-javascript.md)屬性。

 以下是 `symbolHelp` 物件的成員：

- `name` 讀取/寫入。 傳回包含識別碼名稱的字串。

- `symbolType` 讀取/寫入。 傳回表示符號類型的字串。 可能的值包括 Unknown、Boolean、Number、String、Object、Function、Array、Date 和 Regex。

- `symbolDisplayType` 讀取/寫入。 傳回字串，其中包含要顯示的類型名稱。 如果未設定 `symbolDisplayType`，則會使用 `symbolType`。

- `elementType` 讀取/寫入。 如果 `symbolType` 是 `Array`，則會傳回代表陣列中元素類型的字串。

- `scope` 讀取/寫入。 傳回表示符號範圍的字串。 可能的值包括 global、local、parameter 和 member。

- `description` 讀取/寫入。 傳回包含符號描述的字串。

- `locid` 讀取/寫入。 傳回字串識別碼，其中包含符號的當地語系化資訊。

- `helpKeyword` 讀取/寫入。 傳回包含 Help 關鍵字的字串。

- `externalFile` 讀取/寫入。 傳回表示包含成員識別碼之檔案的字串。

- `externalid` 讀取/寫入。 傳回字串，表示符號的成員 ID。

- `functionHelp` 讀取/寫入。 傳回[FunctionHelp 屬性](#FunctionHelp)，其中可能包含 `symbolType` 為函數時的資訊。

### <a name="Scope"></a>scope 屬性
 傳回事件的完成範圍。 完成範圍的可能值為全域和成員。 這個屬性可用於 `statementcompletion` 事件物件。

 傳回值：字串

## <a name="debugging-intellisense-extensions"></a>IntelliSense 擴充功能的調試
 您無法調試延伸模組，但可以使用[Intellisense 物件](#intellisenseObject)函數將資訊傳送至 Visual Studio 的輸出視窗。 如需顯示如何使用此函式的範例，請參閱本主題稍後的傳送[訊息至輸出視窗](#Logging)。 若要讓 `logMessage` 能夠正常執行，至少必須在延伸模組中註冊一個事件處理常式。

## <a name="CodeExamples"></a> 程式碼範例
 本節包含示範如何使用 IntelliSense 擴充性 Api 的程式碼範例。 還有其他使用這些 Api 的方式。 如需其他範例，請參閱 \\ \\*Visual Studio 安裝路徑*\JavaScript\References 資料夾中的下列檔案。 這些是 JavaScript 語言服務所使用的工作範例。

- underscoreFilter.js。 此程式碼會隱藏 IntelliSense 的私用成員。 其中包含 `statementcompletion` 事件的事件處理常式。

- showPlainComments.js。 這段程式碼會提供標準批註的 IntelliSense 支援。 其中包含 `signaturehelp` 和 `statementcompletionhint` 事件的事件處理常式。

### <a name="Annotations"></a>加入 IntelliSense 注釋
 下列程式顯示如何在不直接修改程式庫的情況下，為協力廠商程式庫提供 IntelliSense 檔支援。 若要這樣做，您可以在擴充功能中使用 `intellisense.annotate`。

 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:

- demoLib，這是代表協力廠商程式庫的專案檔。

- demoLib，這是 IntelliSense 延伸模組。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。

- 這個 appCode.js 是代表應用程式程式碼的專案檔。

##### <a name="to-add-an-intellisense-annotation"></a>若要加入 IntelliSense 注釋

1. 將下列程式碼新增至 demoLib。

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. 將下列程式碼加入至 demoLib。

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

4. 在 appCode.js 中，輸入以下程式碼。 您會在延伸模組中看到顯示為 IntelliSense 參數資訊的 XML 檔批註。

     ![示範如何使用 intellisense 的範例。標注](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. 在 appCode.js 中，輸入以下程式碼。 當您輸入時，您會在延伸模組中看到顯示為 IntelliSense 快速諮詢的標準批註。

     ![示範如何使用 intellisense 的範例。標注](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="Logging"></a>將訊息傳送至輸出視窗
 下列程式顯示如何將訊息傳送至 [輸出] 視窗。 您可以傳送訊息以協助 debug IntelliSense 延伸模組。

 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:

- exampleLib，這是代表協力廠商程式庫的專案檔。

- exampleLib，這是 IntelliSense 延伸模組。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。

- 這個 appCode.js 是代表應用程式程式碼的專案檔。

##### <a name="to-send-a-message-to-the-output-window"></a>若要將訊息傳送至輸出視窗

1. 將下列程式碼新增至 exampleLib。

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. 將下列程式碼加入至 exampleLib。

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

4. 在 [輸出] 視窗中，選擇 [**顯示輸出來源**] 清單中的 [ **JavaScript Language Service** ]。 （若要查看 [輸出] 視窗，請從 [View] 功能表選取 [**輸出**]）。

5. 在 appCode.js 中，輸入以下程式碼。 當您輸入時，[輸出] 視窗會顯示來自語言服務的訊息。 [輸出] 視窗中的第一個訊息指出已要求目前範圍的語句完成。

    ```javascript
    some
    ```

     以下是您應該會看到的輸出部分。

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. 選擇 [輸出] 視窗中的 [**全部清除**] 按鈕。

7. 輸入下列程式碼。 [輸出] 視窗中的第一個訊息指出已要求成員清單。

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

### <a name="Icons"></a>變更 IntelliSense 圖示
 下列程式顯示如何變更 IntelliSense 預設顯示的圖示。 當您提供有關程式庫特定概念（例如命名空間、類別、介面和列舉）的 IntelliSense 資訊時，這可能會很有用。

 如需可用的圖示值，請參閱 <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>。

 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:

- exampleLib，這是 represens 協力廠商程式庫的專案檔。

- exampleLib，這是 IntelliSense 延伸模組。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。

- 這個 appCode.js 是代表應用程式程式碼的專案檔。

##### <a name="to-change-the-icons"></a>變更圖示

1. 將下列程式碼新增至 exampleLib。

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

2. 將下列程式碼加入至 exampleLib。

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

4. 在 appCode.js 中，輸入以下程式碼。 當您輸入時，您會看到命名空間的圖示已變更為 "{}"，如同中C#所使用。

     ![顯示使用圖像屬性的範例](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. 在 appCode.js 中，輸入以下程式碼。 當您輸入時，您會看到 Enum1 成員的新列舉圖示，以及 SomeClass1 成員的新類別圖示。

     ![顯示使用圖像屬性的範例](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="Overriding"></a>避免 IntelliSense 結果的執行時間效果
 JavaScript 語言服務會執行程式碼，以動態方式提供 IntelliSense 資訊。 因此，執行時間行為偶爾會干擾所需的結果。 下列程式顯示當執行時間行為導致不正確的 IntelliSense 時，如何覆寫 IntelliSense 結果。

 若要讓範例能夠運作，您的專案需要下列 JavaScript 檔案:

- exampleLib，這是代表協力廠商程式庫的專案檔。

- exampleLib，這是 IntelliSense 延伸模組。 這個檔案不必包含在專案中，但必須與 exampleLib.js 在同一個資料夾。

- 這個 appCode.js 是代表應用程式程式碼的專案檔。

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>避免 IntelliSense 結果的執行時間影響

1. 將下列程式碼新增至 exampleLib。

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     在上述程式碼中，包裝的函式會根據 `count` 的值，忽略初始呼叫，而不會傳回結果。

2. 加入下列參考指示詞，做為 appCode.js 的第一行。 這裡使用的路徑表示 JavaScript 檔案在同一個資料夾中。

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. 在 appCode.js 中，輸入以下程式碼。 [識別碼] 清單會出現而不是 IntelliSense，因為永遠不會呼叫包裝的函式，這表示 `throttled` 函式不會傳回任何結果。

     ![覆寫 intellisense 結果的範例](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. 將下列程式碼加入至 exampleLib。 這會變更設計階段行為，如此就能如預期般顯示已包裝函式的 IntelliSense。

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. 在 Appcode.js 中，輸入您先前輸入的相同程式碼來測試結果。 這次，IntelliSense 會提供所需的資訊。

     ![覆寫 IntelliSense 結果的範例](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>請參閱
 識別碼的[JavaScript IntelliSense](../ide/javascript-intellisense.md) [語句完成](../ide/statement-completion-for-identifiers.md)
