---
description: 嘗試以不正確引數叫用 json.stringify。
title: 不正確取代子引數 |Microsoft 檔
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 95a73d6fcbcf1350eece52e2cd58693646617a28
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570891"
---
# <a name="invalid-replacer-argument"></a>無效的取代子引數
嘗試使用不正確 `JSON.stringify` 引數進行叫用。 `replacer`引數必須是函式或陣列。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將 `replacer` 引數變更為函式或陣列。  
  
## <a name="example"></a>範例  
 此範例中的程式碼會造成執行階段錯誤，因為 `memberfilter` 是物件，而不是函式或陣列。  
  
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
 [JSON 物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON. parse 函數](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [JavaScript 執行階段錯誤](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
