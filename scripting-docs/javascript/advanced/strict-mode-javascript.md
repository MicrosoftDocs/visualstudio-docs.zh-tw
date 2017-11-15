---
title: "strict 模式 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="strict-mode-javascript"></a>strict 模式 (JavaScript)
檢查程式碼錯誤時，使用 strict 模式可獲得較佳的效果。 例如，當您使用 strict 模式時，就不能使用隱含宣告的變數或將值指派給唯讀屬性，也不能為無法擴充的物件添加屬性。 本主題稍後的[程式碼在 strict 模式下的限制](../../javascript/advanced/strict-mode-javascript.md#rest)一節中會列出這些限制。 如需 strict 模式的詳細資訊，請參閱 [ECMAScript 語言規格，第 5 版](http://www.ecma-international.org/publications/standards/Ecma-262.htm)。  
  
> [!WARNING]
>  Internet Explorer 10 之前的 Internet Explorer 版本不支援 strict 模式。  
  
## <a name="declaring-strict-mode"></a>宣告 strict 模式  
 您可以在檔案、程式或函式的開頭加上 `"use strict";` 宣告 strict 模式。 這類宣告稱為「指示詞序言」。 strict 模式宣告的範圍取決於宣告本身的內容。 如果在全域內容中 (在函式範圍之外) 宣告，則程式中的所有程式碼都會套用 strict 模式； 如果是在函式宣告，則函式中的所有程式碼都會套用 strict 模式。 例如，下面範例中的所有程式碼都會套用 strict 模式，因此在函式以外的變數宣告都會發生「未在 strict 模式中定義此變數」語法錯誤。  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 在下面範例中，只有 `testFunction` 內的程式碼才會套用 strict 模式。 函式以外的變數宣告不會導致語法錯誤，但是函式中的宣告則會。  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>程式碼在 strict 模式下的限制  
 下表列出程式碼在 strict 模式下所受到最重要的限制。  
  
|||||  
|-|-|-|-|  
|**語言項目**|**限制**|**錯誤**|**範例**|  
|變數|使用未宣告的變數。|SCRIPT5042：未在 strict 模式中定義此變數|`testvar = 4;`|  
|唯讀屬性|寫入至唯讀屬性。|SCRIPT5045：不可在 strict 模式中指派唯讀屬性|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|無法擴充的屬性 (Property)|為 `extensible` 屬性 (Attribute) 已設定為 `false` 的物件添加屬性 (Property)。|SCRIPT5046：不可為無法延伸的物件建立屬性|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|刪除變數、函式或引數。<br /><br /> 刪除 `configurable` 屬性 (Attribute) 已設定為 `false` 的屬性 (Property)。|SCRIPT1045：strict 模式中不允許在 \<運算式> 上呼叫刪除|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|複製屬性 (Property)|在物件常值中多次定義屬性 (Property)。|SCRIPT1046：strict 模式中不允許屬性有多個定義|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|複製參數名稱|在函式中多次使用參數名稱。|SCRIPT1038：strict 模式中不允許重複的型式參數名稱|`function testFunc(param1, param1) {     return 1; };`|  
|未來保留的關鍵字|使用未來保留的關鍵字做為變數或函式名稱。|SCRIPT1050：使用未來供識別項使用的保留字是無效的動作。 在 strict 模式中識別項名稱是保留字。|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|八進位值|將八進位值指派給數字常值，或嘗試逸出八進位值。|SCRIPT1039：strict 模式中不允許八進位數值常值和逸出字元|`var testoctal = 010; var testescape = \010;`|  
|`this`|如果 `this` 的值是 `null` 或 `undefined`，就無法轉換成全域物件。||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> 如果不是在 strict 模式下，`testvar` 的值是全域物件，但是其值在 strict 模式下則是 `undefined`。|  
|當做識別項的 `eval`|"eval" 這個字串不能當做識別項 (變數或函式名稱、參數名稱等等)。||`var eval = 10;`|  
|在陳述式或區塊內宣告的函式|您無法在陳述式或區塊內宣告函式。|SCRIPT1047：在 strict 模式中，函式宣告不可以巢狀在陳述式或區塊內部。 它們只可以出現在最上層或直接位於函式主體內。|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|在 `eval` 函式內宣告的變數|如果是在 `eval` 函式中宣告變數，您就不能在函式外部使用該變數。|SCRIPT1041：strict 模式中 'eval' 的使用方式無效|`eval("var testvar = 10"); testvar = 15;`<br /><br /> 雖然可以間接評估，但是您仍然無法使用在 `eval` 函式外部宣告的變數。<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> 上述程式碼會造成錯誤 SCRIPT5009：'testVar' 未經定義。|  
|當做識別項的 `Arguments`|"arguments" 這個字串不能當做識別項 (變數或函式名稱、參數名稱等等)。|SCRIPT1042：strict 模式中 'arguments' 的使用方式無效|`var arguments = 10;`|  
|位於函式內的 `arguments`|您無法變更區域 `arguments` 物件成員的值。||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> 如果不是在 strict 模式下，您可以變更 `oneArg` 的值來變更 `arguments[0]` 參數的值，因此 `oneArg` 和 `arguments[0]` 的值都是 20； 在 strict 模式下，因為 `arguments[0]` 物件只是區域複本，所以變更 `oneArg` 的值並不會影響 `arguments` 的值。|  
|`arguments.callee`|不允許。||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|不允許。|SCRIPT1037：strict 模式中不允許 'with' 陳述式|`with (Math){     x = cos(3);     y = tan(7); }`|