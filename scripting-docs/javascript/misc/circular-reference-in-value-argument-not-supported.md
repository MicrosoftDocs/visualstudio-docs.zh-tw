---
title: 不支援值引數中的迴圈參考 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 633ed9c37e8ccde0844205910a8fa2dc12d91414
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817615"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>不支援數值引數中的循環參考
嘗試使用不正確 `JSON.stringify` 值叫用。 `value`引數（陣列或物件）包含迴圈參考。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 從引數中移除迴圈參考。  
  
## <a name="example"></a>範例  
 此範例中的程式碼會造成執行階段錯誤 `john` ，因為具有的參考 `mary` ，而且 `mary` 具有的參考 `john` 。 若要移除迴圈參考，請 `brother` 從物件 `mary` 或 `sister` 從物件的屬性中移除或取消設定屬性 `john` 。  
  
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
 [JSON. parse 函式](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript 執行階段錯誤](../../javascript/reference/javascript-run-time-errors.md)