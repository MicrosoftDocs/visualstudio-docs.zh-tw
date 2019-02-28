---
title: 不支援的數值引數中的循環參考 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1235c8b1bb7b815b5f26e0ffb744c31a3575ba81
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841087"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>不支援數值引數中的循環參考
已嘗試叫用`JSON.stringify`不是有效的值。 `value`引數、 陣列或物件，包含循環參考。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除引數中的循環參考。  
  
## <a name="example"></a>範例  
 在此範例中的程式碼會造成執行階段錯誤，因為`john`參考`mary`並`mary`具有指向`john`。 若要移除循環參考，請移除或取消設定的屬性`brother`從`mary`物件或`sister`屬性從`john`物件。  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>另請參閱  
 [JSON 物件](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript 執行階段錯誤](../../javascript/reference/javascript-run-time-errors.md)