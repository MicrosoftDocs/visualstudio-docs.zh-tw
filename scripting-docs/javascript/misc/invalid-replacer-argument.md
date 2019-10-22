---
title: 不正確取代子引數 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ba76a2121dfb3853e38bacbdf49c985103c2a35
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573802"
---
# <a name="invalid-replacer-argument"></a>無效的取代子引數
嘗試使用不正確引數來叫用 `JSON.stringify`。 @No__t_0 引數必須是函式或陣列。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將 `replacer` 引數變更為函式或陣列。  
  
## <a name="example"></a>範例  
 這個範例中的程式碼會造成執行階段錯誤，因為 `memberfilter` 是物件，而不是函式或陣列。  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>請參閱  
 [JSON 物件](../../javascript/reference/json-object-javascript.md)   
 [JSON. parse](../../javascript/reference/json-parse-function-javascript.md)函式    
 [JavaScript 執行階段錯誤](../../javascript/reference/javascript-run-time-errors.md)