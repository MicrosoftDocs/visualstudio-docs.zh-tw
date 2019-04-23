---
title: 無效的取代子引數 |Microsoft Docs
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
ms.openlocfilehash: 46e01a4e6bb989fad2da6f979c79b7aba13df63a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060783"
---
# <a name="invalid-replacer-argument"></a>無效的取代子引數
已嘗試叫用`JSON.stringify`不是有效的引數。 `replacer`引數必須是函式或陣列。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 變更`replacer`函式或陣列引數。  
  
## <a name="example"></a>範例  
 在此範例中的程式碼會造成執行階段錯誤，因為`memberfilter`是一個物件，而不是函式或陣列。  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>另請參閱  
 [JSON 物件](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript 執行階段錯誤](../../javascript/reference/javascript-run-time-errors.md)