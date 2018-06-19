---
title: JavaScript 版本資訊 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, version information
ms.assetid: 440f4924-f7a9-48e0-873e-bd599a93b437
caps.latest.revision: 93
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a2335c3697be9ef3e2d674ac37047ddd3de242d
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
ms.locfileid: "29753493"
---
# <a name="javascript-version-information"></a>JavaScript 版本資訊
不同的 JavaScript 版本支援不同的 JavaScript 項目集。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式與 Internet Explorer 支援的功能集略有不同。  
  
> [!IMPORTANT]
>  [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式是一種新型應用程式，可在 [!INCLUDE[win8](../../javascript/includes/win8-md.md)] 裝置上執行。 若要深入了解 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式，請參閱 [What's a Windows Store app?](http://msdn.microsoft.com/en-us/231c1fba-9f87-468e-94aa-45dd57edcc70)  
  
 標準模式 (Internet Explorer 11 前的所有 Internet Explorer 版本中都有 `<!doctype>` 指示詞時所使用的模式) 支援的項目集也與 Quirks 模式 (沒有 `<!doctype>` 指示詞時使用的模式) 支援的項目集不同。 如需版本控制的詳細資訊，請參閱 [Defining Document Compatibility (定義文件相容性)](http://go.microsoft.com/fwlink/?LinkId=208537)。  
  
 下表列出支援特定語言項目的 Internet Explorer 文件模式 (以及代表 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 和 [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)]的市集應用程式)。 支援特定項目的文件模式會以字母 **Y**表示，而不支援特定項目的文件模式則會以字母 **N**表示。  
  
> [!IMPORTANT]
>  [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] （在 Windows 10 中的 edge 瀏覽器） 不包含支援舊版文件模式。 從 Windows Phone 8.1 開始的 [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)] 應用程式支援這種模式。 實驗功能 (關於： flags) 以"exp 表示。  
  
 此表格包含摘要資訊。 如需特定資訊，請參閱語言項目的文件。  
  
|語言項目|Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準|Internet Explorer 8 標準|Internet Explorer 9 標準|Internet Explorer 10 標準|Internet Explorer 11 標準|Edge|市集應用程式|  
|----------------------|--------------------------------------------------------------------------|-----------------------------------|-----------------------------------|------------------------------------|------------------------------------|----------|----------------|  
|[__proto\_ \_屬性 (Object)](../../javascript/reference/proto-property-object-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[$1...$9 Properties (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[0n 屬性](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[abs 函式](../../javascript/reference/math-abs-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[acos 函式](../../javascript/reference/math-acos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[acosh 函式](../../javascript/reference/math-acosh-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[ActiveXObject 物件](../../javascript/reference/activexobject-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[加法設定運算子 (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[加法運算子 (+)](../../javascript/reference/addition-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[apply 方法](../../javascript/reference/apply-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[arguments 物件](../../javascript/reference/arguments-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[arguments 屬性](../../javascript/reference/arguments-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Array 物件](../../javascript/reference/array-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Array.from 函式 (Array)](../../javascript/reference/array-from-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Array.isArray 函式](../../javascript/reference/array-isarray-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Array.of 函式 (Array)](../../javascript/reference/array-of-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)|N|N|N|Y|Y|Y|Y|  
|[函式](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[asin 函式](../../javascript/reference/math-asin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Object.assign 函式 (Object)](../../javascript/reference/object-assign-function-object-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[設定運算子 (=)](../../javascript/reference/assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[atan 函式](../../javascript/reference/math-atan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[atan2 函式](../../javascript/reference/math-atan2-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[atEnd 方法](../../javascript/reference/atend-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[bind 方法](../../javascript/reference/bind-method-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[位元 AND 指派運算子 (&=)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[位元 AND 運算子 (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[位元左移運算子 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[位元 NOT 運算子 (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[位元 OR 指派運算子 (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[位元 OR 運算子 (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[位元右移運算子 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[位元 YOR 指派運算子 (^=)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[位元 YOR 運算子 (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[blink 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[bold 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Boolean 物件](../../javascript/reference/boolean-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[break 陳述式](../../javascript/reference/break-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[call 方法](../../javascript/reference/call-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[callee 屬性](../../javascript/reference/callee-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[caller 屬性](../../javascript/reference/caller-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[catch 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ceil 函式](../../javascript/reference/math-ceil-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[charAt 方法](../../javascript/reference/charat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[charCodeAt 方法](../../javascript/reference/charcodeat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[class 陳述式](../../javascript/reference/class-statement-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[codePointAt 方法 (字串)](../../javascript/reference/codepointat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[逗號運算子 (,)](../../javascript/reference/comma-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[// (單行註解陳述式)](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[/*..\*/ （多行註解陳述式）](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[比較運算子](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[compile 方法](../../javascript/reference/compile-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[concat 方法 (陣列)](../../javascript/reference/concat-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[concat 方法 (字串)](../../javascript/reference/concat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[條件 (三元) 運算子 (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[constructor 屬性](../../javascript/reference/constructor-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[const 陳述式](../../javascript/reference/const-statement-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[continue 陳述式](../../javascript/reference/continue-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[cos 函式](../../javascript/reference/math-cos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[create 函式](../../javascript/reference/object-create-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[DataView 物件](../../javascript/reference/dataview-object.md)|N|N|N|Y|Y|Y|Y|  
|[Date 物件](../../javascript/reference/date-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Debug 物件](../../javascript/reference/debug-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Debug.setNonUserCodeExceptions 屬性](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|Y|Y|Y|Y|  
|[Debug.setNonUserCodeExceptions 屬性](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|Y|Y|Y|Y|  
|[debugger 陳述式](../../javascript/reference/debugger-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[DecodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[遞減運算子 (--)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[函式](../../javascript/functions-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[defineProperties 函式](../../javascript/reference/object-defineproperties-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[delete 運算子](../../javascript/reference/delete-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[description 屬性](../../javascript/reference/description-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[dimensions 方法](../../javascript/reference/dimensions-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[除法設定運算子 (/=)](../../javascript/reference/division-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[除法運算子 (/)](../../javascript/reference/division-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[do...while 陳述式](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[E 常數](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[encodeURI 元件函式](../../javascript/reference/encodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[entries 方法 (Array)](../../javascript/reference/entries-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Enumerator 物件](../../javascript/reference/enumerator-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Number 常數](../../javascript/reference/number-constants-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[等號比較運算子 (==)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Error 物件](../../javascript/reference/error-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[stack 屬性 (Error)](../../javascript/reference/stack-property-error-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[stackTraceLimit 屬性 (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[escape 函式](../../javascript/reference/escape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[eval 函式](../../javascript/reference/eval-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[exec 方法](../../javascript/reference/exec-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[every 方法](../../javascript/reference/every-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[exp 函式](../../javascript/reference/math-exp-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[fill 方法 (Array)](../../javascript/reference/fill-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[filter 方法](../../javascript/reference/filter-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[findIndex 方法 (Array)](../../javascript/reference/findindex-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[fixed 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Float32Array 物件](../../javascript/reference/float32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Float64Array 物件](../../javascript/reference/float64array-object.md)|N|N|N|Y|Y|Y|Y|  
|[floor 函式](../../javascript/reference/math-floor-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[fontcolor 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[fontsize 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[for 陳述式](../../javascript/reference/for-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[forEach 方法](../../javascript/reference/foreach-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[for...in 陳述式](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[for...of 陳述式](../../javascript/reference/for-dot-dot-dot-of-statement-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[freeze 函式](../../javascript/reference/object-freeze-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[fromCharCode 函式](../../javascript/reference/string-fromcharcode-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[fromCodePoint 函式](../../javascript/reference/string-fromcodepoint-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Function 物件](../../javascript/reference/function-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[function 陳述式](../../javascript/reference/function-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[產生器](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[getDate 方法](../../javascript/reference/getdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getDay 方法](../../javascript/reference/getday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getFullYear 方法](../../javascript/reference/getfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getHours 方法](../../javascript/reference/gethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getItem 方法](../../javascript/reference/getitem-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getMilliseconds 方法](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getMinutes 方法](../../javascript/reference/getminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getMonth 方法](../../javascript/reference/getmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[GetObject 函式](../../javascript/reference/getobject-function-javascript.md)|Y|Y|N|N|N|N|N|  
|[getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[getPrototypeOf 函式](../../javascript/reference/object-getprototypeof-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[getSeconds 方法](../../javascript/reference/getseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getTime 方法](../../javascript/reference/gettime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getTimezoneOffset 方法](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCDate 方法](../../javascript/reference/getutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCDay 方法](../../javascript/reference/getutcday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCFullYear 方法](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCHours 方法](../../javascript/reference/getutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCMilliseconds 方法](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCMinutes 方法](../../javascript/reference/getutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCMonth 方法](../../javascript/reference/getutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCSeconds 方法](../../javascript/reference/getutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getVarDate 方法](../../javascript/reference/getvardate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[getYear 方法](../../javascript/reference/getyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Global 物件](../../javascript/reference/global-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[global 屬性](../../javascript/reference/global-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[大於運算子 (>)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[大於或等於運算子 (>=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[HTML 標記方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[hypot 函式](../../javascript/reference/math-hypot-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[識別運算子 (===)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[if...else 陳述式](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ignoreCase 屬性](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[imul 函式](../../javascript/reference/math-imul-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[In 運算子](../../javascript/reference/in-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[includes 方法 (字串)](../../javascript/reference/includes-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[遞增運算子 (++)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[index 屬性](../../javascript/reference/index-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[indexOf 方法 (Array)](../../javascript/reference/indexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[indexOf 方法 (字串)](../../javascript/reference/indexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[不等比較運算子 (!=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Infinity 常數](../../javascript/reference/infinity-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[input 屬性 ($_)](../../javascript/reference/input-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[instanceof 運算子](../../javascript/reference/instanceof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Int8Array 物件](../../javascript/reference/int8array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Int16Array 物件](../../javascript/reference/int16array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Int32Array 物件](../../javascript/reference/int32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Intl.Collator 物件](../../javascript/reference/intl-collator-object-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[Intl.DateTimeFormat 物件](../../javascript/reference/intl-datetimeformat-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Intl.NumberFormat 物件](../../javascript/reference/intl-numberformat-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[isFinite 函式](../../javascript/reference/isfinite-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[isArray 函式](../../javascript/reference/array-isarray-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[IsExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[isFrozen 函式](../../javascript/reference/object-isfrozen-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[isInteger 函式](../../javascript/reference/number-isinteger-function-number-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[isNaN 函式](../../javascript/reference/isnan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[isNaN 函式 (數字)](../../javascript/reference/number-isnan-function-number-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[ISO 日期格式](../../javascript/date-and-time-strings-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[IsPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[isSealed 函式](../../javascript/reference/object-issealed-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[italics 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Iterator](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[item 方法](../../javascript/reference/item-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[join 方法](../../javascript/reference/join-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[JSON 物件](../../javascript/reference/json-object-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[keys 函式](../../javascript/reference/object-keys-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[keys 方法 (Array)](../../javascript/reference/keys-method-array-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Labeled 陳述式](../../javascript/reference/labeled-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lastIndex 屬性](../../javascript/reference/lastindex-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lastIndexOf 方法 (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[lastIndexOf 方法 (字串)](../../javascript/reference/lastindexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lastMatch 屬性 ($&)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lastParen 屬性 ($+)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lbound 方法](../../javascript/reference/lbound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[leftContext 屬性 ($')](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[左移設定運算子 (<<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[length 屬性 (引數)](../../javascript/reference/length-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[length 屬性 (陣列)](../../javascript/reference/length-property-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[length 屬性 (函式)](../../javascript/reference/length-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[length 屬性 (字串)](../../javascript/reference/length-property-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[小於運算子 (<)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[小於或等於運算子 (<=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[let 陳述式](../../javascript/reference/let-statement-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[link 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[LN2 常數](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[LN10 常數](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[localeCompare 方法](../../javascript/reference/localecompare-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[log 函式](../../javascript/reference/math-log-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[LOG2E 常數](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[LOG10E 常數](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[邏輯 AND 運算子 (&&)](../../javascript/reference/logical-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[邏輯 NOT 運算子 (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[邏輯 OR 運算子 (&#124; &#124;)](../../javascript/reference/logical-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[map 方法](../../javascript/reference/map-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Map 物件](../../javascript/reference/map-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[match 方法](../../javascript/reference/match-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Math 物件](../../javascript/reference/math-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[max 函式](../../javascript/reference/math-max-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[MAX_VALUE 常數](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[message 屬性](../../javascript/reference/message-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[min 函式](../../javascript/reference/math-min-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[MIN_VALUE 常數](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[餘數設定運算子 (%=)](../../javascript/reference/modulus-assignment-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[餘數運算子 （%）](../../javascript/reference/modulus-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[moveFirst 方法](../../javascript/reference/movefirst-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[moveNext 方法](../../javascript/reference/movenext-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[multiline 屬性](../../javascript/reference/multiline-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[乘法設定運算子 (*=)](../../javascript/reference/multiplication-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[乘法運算子 (*)](../../javascript/reference/multiplication-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[name 屬性](../../javascript/reference/name-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[NaN 常數 (全域)](../../javascript/reference/nan-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[NaN 常數 (數字)](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[NEGATIVE_INFINITY 常數](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[非識別運算子 (!==)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[now 函式](../../javascript/reference/date-now-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Number 物件](../../javascript/reference/number-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[number 屬性](../../javascript/reference/number-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Object 物件](../../javascript/reference/object-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Date.parse 函式](../../javascript/reference/date-parse-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[parseFloat 函式](../../javascript/reference/parsefloat-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[parseInt 函式](../../javascript/reference/parseint-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[PI 常數](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[pop 方法](../../javascript/reference/pop-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[POSITIVE_INFINITY 常數](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[pow 函式](../../javascript/reference/math-pow-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Promise 物件](../../javascript/reference/promise-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[prototype 屬性](../../javascript/reference/prototype-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proxy 物件](../../javascript/reference/proxy-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[push 方法](../../javascript/reference/push-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[random 函式](../../javascript/reference/math-random-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[raw 函式](../../javascript/reference/string-raw-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[reduce 方法](../../javascript/reference/reduce-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[reduceRight 方法](../../javascript/reference/reduceright-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[RegExp 物件](../../javascript/reference/regexp-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[規則運算式語法](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)|Y|Y|Y|Y|Y|Y|Y|  
|[規則運算式 /y 旗標](../../javascript/reference/regular-expression-object-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[repeat 方法 (字串)](../../javascript/reference/repeat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[replace 方法](../../javascript/reference/replace-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[函式](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[return 陳述式](../../javascript/reference/return-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[reverse 方法](../../javascript/reference/reverse-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[rightContext 屬性 ($')](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[右移設定運算子 (>>=)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[round 函式](../../javascript/reference/math-round-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ScriptEngine 函式](../../javascript/reference/scriptengine-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ScriptEngineBuildVersion 函式](../../javascript/reference/scriptenginebuildversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ScriptEngineMajorVersion 函式](../../javascript/reference/scriptenginemajorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ScriptEngineMinorVersion 函式](../../javascript/reference/scriptengineminorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[seal 函式](../../javascript/reference/object-seal-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[search 方法](../../javascript/reference/search-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Set 物件](../../javascript/reference/set-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[setDate 方法](../../javascript/reference/setdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setFullYear 方法](../../javascript/reference/setfullyear-method-date-javascript.md)||Y|Y|Y|Y|Y|Y|  
|[setHours 方法](../../javascript/reference/sethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setMilliseconds 方法](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setMinutes 方法](../../javascript/reference/setminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setMonth 方法](../../javascript/reference/setmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setSeconds 方法](../../javascript/reference/setseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setTime 方法](../../javascript/reference/settime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCDate 方法](../../javascript/reference/setutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCFullYear 方法](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCHours 方法](../../javascript/reference/setutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCMilliseconds 方法](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCMinutes 方法](../../javascript/reference/setutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCMonth 方法](../../javascript/reference/setutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCSeconds 方法](../../javascript/reference/setutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setYear 方法](../../javascript/reference/setyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[shift 方法](../../javascript/reference/shift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[sin 函式](../../javascript/reference/math-sin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[slice 方法 (陣列)](../../javascript/reference/slice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[slice 方法 (字串)](../../javascript/reference/slice-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[small 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[some 方法](../../javascript/reference/some-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[sort 方法](../../javascript/reference/sort-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[source 屬性](../../javascript/reference/source-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[splice 方法](../../javascript/reference/splice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[split 方法](../../javascript/reference/split-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[函式](../../javascript/functions-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[sqrt 函式](../../javascript/reference/math-sqrt-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[SQRT1_2 常數](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[SQRT2 常數](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[use strict 指示詞](../../javascript/reference/use-strict-directive.md)|N|N|N|Y|Y|Y|Y|  
|[strike 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[String 物件](../../javascript/reference/string-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[JSON.stringify 函式](../../javascript/reference/json-stringify-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[sub 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[substr 方法](../../javascript/reference/substr-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[substring 方法](../../javascript/reference/substring-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[減法設定運算子 (-=)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[減法運算子 (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[sup 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[switch 陳述式](../../javascript/reference/switch-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[符號物件](../../javascript/reference/symbol-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[tan 函式](../../javascript/reference/math-tan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[範本字串](../../javascript/advanced/template-strings-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[test 方法](../../javascript/reference/test-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[this 陳述式](../../javascript/reference/this-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[throw 陳述式](../../javascript/reference/throw-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toArray 方法](../../javascript/reference/toarray-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toDateString 方法](../../javascript/reference/todatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toExponential 方法](../../javascript/reference/toexponential-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toFixed 方法](../../javascript/reference/tofixed-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toGMTString 方法](../../javascript/reference/togmtstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toISOString 方法](../../javascript/reference/toisostring-method-date-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[toJSON 方法](../../javascript/reference/tojson-method-date-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[toLocaleDateString 方法](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLocaleLowercase 方法](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLocaleTimeString 方法](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLocaleUppercase 方法](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLowerCase 方法](../../javascript/reference/tolowercase-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toPrecision 方法](../../javascript/reference/toprecision-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toString 方法](../../javascript/reference/tostring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toTimeString 方法](../../javascript/reference/totimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toUpperCase 方法](../../javascript/reference/touppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toUTCString 方法](../../javascript/reference/toutcstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[trim 方法](../../javascript/reference/trim-method-string-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[try 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[typeof 運算子](../../javascript/reference/typeof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ubound 方法](../../javascript/reference/ubound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Uint8Array 物件](../../javascript/reference/uint8array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Uint16Array 物件](../../javascript/reference/uint16array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Uint32Array 物件](../../javascript/reference/uint32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Uint8ClampedArray 物件](../../javascript/reference/uint8clampedarray-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1 (Win): Y<br />v8.1 (Phone): N<br />v10: Y|  
|[一元負運算子 (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[undefined 常數](../../javascript/reference/undefined-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[unescape 函式](../../javascript/reference/unescape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Unicode 字碼指標逸出字元](../../javascript/advanced/special-characters-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[unshift 方法](../../javascript/reference/unshift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[不帶正負號的右移設定運算子 (>>>=)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[不帶正負號的右移運算子 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[use strict 指示詞](../../javascript/reference/use-strict-directive.md)|N|N|N|Y|Y|Y|Y|  
|[UTC 函式](../../javascript/reference/date-utc-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[values 方法 (Array)](../../javascript/reference/values-method-array-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[var 陳述式](../../javascript/reference/var-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[VBArray 物件](../../javascript/reference/vbarray-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[void 運算子](../../javascript/reference/void-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[WeakMap 物件](../../javascript/reference/weakmap-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[WeakSet 物件](../../javascript/reference/weakset-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[while 陳述式](../../javascript/reference/while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[WinRTError 物件](../../javascript/reference/winrterror-object-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[with 陳述式](../../javascript/reference/with-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[write 函式](../../javascript/reference/debug-write-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[writeln 函式](../../javascript/reference/debug-writeln-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
  
 \* 支援 DOM 物件，但沒有使用者定義的物件。 `enumerable` 和 `configurable` 屬性都可以指定，但是不會使用。  
  
## <a name="see-also"></a>請參閱  
 [Defining Document Compatibility (定義文件相容性)](http://go.microsoft.com/fwlink/?LinkId=208537)