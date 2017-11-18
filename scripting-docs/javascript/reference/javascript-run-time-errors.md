---
title: "JavaScript 執行階段錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT-32725
- VS.WebClient.Help.SCRIPT7002
- VS.WebClient.Help.SCRIPT1001
- VS.WebClient.Help.SCRIPT16389
- VS.WebClient.HelpSCRIPT50
- VS.WebClient.HelpSCRIPT70
- VS.WebClient.HelpSCRIPT87
- VS.WebClient.HelpSCRIPT65535
- VS.WebClient.HelpSCRIPT445
- VS.WebClient.HelpSCRIPT600
- VS.WebClient.HelpSCRIPT2343
- VS.WebClient.HelpSCRIPT122
- VS.WebClient.HelpSCRIPT28
- VS.WebClient.HelpSCRIPT16386
- VS.WebClient.HelpSCRIPT7015
- VS.WebClient.HelpSCRIPT3
- VS.WebClient.HelpSCRIPT16388
- VS.WebClient.HelpSCRIPT14
- VS.WebClient.HelpSCRIPT12030
- VS.WebClient.HelpSCRIPT12029
- VS.WebClient.HelpSCRIPT1001
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- run-time errors, JavaScript
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb75c59fae32911c3dd3a7468439a198d7191755
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-run-time-errors"></a>JavaScript 執行階段錯誤
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 執行階段錯誤是指令碼嘗試執行系統無法執行的動作時發生的錯誤。 您可能會在評估變數運算式或配置記憶體時發現執行階段錯誤。  
  
## <a name="windows-runtime-errors"></a>Windows 執行階段錯誤  
 如果您在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式中使用 Windows Runtime API，可能會發現已從 Windows Runtime HRESULT 轉換的 JavaScript 錯誤。 0x80070000 以上範圍中的 Windows 執行階段 HRESULT 會轉換為 JavaScript 錯誤，方法是取得低位元的十六進位值並將它轉換為十進位。 例如，HRESULT 0x80070032 會轉換為十進位值 50，而且 JavaScript 錯誤是 SCRIPT50。 HRESULT 0x80074005 會轉換為十進位值 16389，而且 JavaScript 錯誤是 SCRIPT16389。  
  
## <a name="errors"></a>錯誤  
  
|錯誤號碼|描述|  
|------------------|-----------------|  
|5|[存取遭拒。](../../javascript/misc/access-is-denied.md)|  
|438|[物件不支援此屬性或方法](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|記憶體不足|  
|5029|[陣列長度必須是有限的正整數](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[陣列長度必須被指派為有限的正值](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[必須是陣列或引數物件](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[必須是布林](../../javascript/misc/boolean-expected.md)|  
|5003|[無法指派給函式結果](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|[無法指派給 'this'](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[不支援數值引數中的循環參考](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[必須是日期物件](../../javascript/misc/date-object-expected.md)|  
|5015|[必須是列舉值物件](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[發生例外狀況而且未攔截](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|[在規則運算式中必須是 ')'](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|[必須是 ' &#93;' 中的規則運算式](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[函式沒有有效的原型物件](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[必須是函式](../../javascript/misc/function-expected.md)|  
|5008|[無效的指派](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[不正確的字元集範圍](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[無效的取代子引數](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[必須是 JavaScript 物件](../../javascript/misc/javascript-object-expected.md)|  
|5001|[必須是數字](../../javascript/misc/number-expected.md)|  
|5007|[必須是物件](../../javascript/misc/object-expected.md)|  
|5012|[必須是物件成員](../../javascript/misc/object-member-expected.md)|  
|5016|[必須是規則運算式物件](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[必須是字串](../../javascript/misc/string-expected.md)|  
|5017|[規則運算式中的語法錯誤](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[小數點後數字的數目超過範圍](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[整數位數超過範圍](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[要解碼的 URI 不是有效的編碼](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[要編碼的 URI 包含無效的字元](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[未定義的識別項](../../javascript/misc/undefined-identifier.md)|  
|5018|[非預期的數量詞](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[必須是 VBArray](../../javascript/misc/vbarray-expected.md)|  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 語法錯誤](../../javascript/reference/javascript-syntax-errors.md)