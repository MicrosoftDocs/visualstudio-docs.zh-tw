---
title: JavaScript 語法錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- syntax errors, JavaScript
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc3398d6a90ef308fd2b4b367bc1006ad95f5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639778"
---
# <a name="javascript-syntax-errors"></a>JavaScript 語法錯誤
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]發生語法錯誤時的其中一個結構您[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]陳述式違反一或多個語法的規則。  
  
## <a name="errors"></a>錯誤  
  
|錯誤號碼|描述|  
|------------------|-----------------|  
|1019|[迴圈外不可以有 'break'](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[迴圈外不可以有 'continue'](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[條件式編譯已經關閉](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|['switch' 陳述式中，'default' 僅能出現一次](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[必須是 ' ('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[必須是 ')'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[必須是 '/'](../../javascript/misc/expected-minus.md)|  
|1003|[必須是 ':'](../../javascript/misc/expected-colon.md)|  
|1004|[必須是 ';'](../../javascript/misc/expected-semicolon.md)|  
|1032|[必須是 '@'](../../javascript/misc/expected-at.md)|  
|1029|[必須是 '@end'](../../javascript/misc/expected-at-end.md)|  
|1007|[必須是 ' &#93;'](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[必須是 '{'](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[必須是 '}'](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|[必須是 '='](../../javascript/misc/expected-equal-javascript.md)|  
|1033|[必須是 'catch'](../../javascript/misc/expected-catch.md)|  
|1031|[必須是常數](../../javascript/misc/expected-constant.md)|  
|1023|[必須是十六進位數](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[必須是識別項](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[必須是識別項、字串或數字](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[必須是 'while'](../../javascript/misc/expected-while.md)|  
|1014|[無效的字元](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[找不到標籤](../../javascript/misc/label-not-found.md)|  
|1025|[已重新定義標籤](../../javascript/misc/label-redefined.md)|  
|1018|[函式外部的 'return' 陳述式](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[語法錯誤](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[throw 必須接著一運算式，且於同一行程式碼](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[未結束的註解](../../javascript/misc/unterminated-comment.md)|  
|1015|[未結束的字串常數](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### <a name="script-host-errors"></a>指令碼主機錯誤  
 下列的錯誤會正確說話 script host 相關的錯誤，但您可能偶爾會看到它們。  
  
|錯誤|HRESULT|描述|  
|-----------|-------------|-----------------|  
|SCRIPT_E_RECORDED|0x86664004|若要在指令碼引擎和主機之間傳遞已記錄錯誤。 主機必須傳遞給呼叫者的錯誤碼。|  
|SCRIPT_E_REPORTED|0x80020101|指令碼引擎報告主機可透過 IActiveScriptSite::OnScriptError 處理的例外狀況。 主機可以忽略此錯誤。|  
|SCRIPT_E_PROPAGATE|0x8002010|指令碼錯誤可能是在不同執行緒中呼叫端傳播所造成。 主應用程式應將錯誤碼傳遞給呼叫者。|  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 執行階段錯誤](../../javascript/reference/javascript-run-time-errors.md)