---
title: 不支援值引數中的迴圈參考 |Microsoft Docs
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
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572344"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>不支援數值引數中的循環參考
嘗試使用不正確值叫用 `JSON.stringify`。 @No__t_0 引數、陣列或物件，都包含迴圈參考。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 從引數中移除迴圈參考。  
  
## <a name="example"></a>範例  
 此範例中的程式碼會造成執行階段錯誤，因為 `john` 具有 `mary` 的參考，而且 `mary` 具有 `john` 的參考。 若要移除迴圈參考，請從 `mary` 物件或 `john` 物件的 `sister` 屬性，移除或取消設定屬性 `brother`。  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>請參閱  
 [JSON 物件](../../javascript/reference/json-object-javascript.md)   
 [JSON. parse](../../javascript/reference/json-parse-function-javascript.md)函式    
 [JavaScript 執行階段錯誤](../../javascript/reference/javascript-run-time-errors.md)