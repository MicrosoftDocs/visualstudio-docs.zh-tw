---
title: 必須是函式 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41d1ecc982dcdc4d494fc167e4784e9121bec15e
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843931"
---
# <a name="function-expected"></a>必須是函式
可能是您嘗試叫用的其中一個**函式原型**不是物件上的方法`Function`物件，或您的物件則會在函式呼叫內容中使用。 例如，下列程式碼會產生這個錯誤因為**範例**不是函式。  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   只呼叫**函式原型**上的方法`Function`物件。  
  
-   請確定您使用函式呼叫運算子`()`只有函式來呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [函式物件](../../javascript/reference/function-object-javascript.md)   
 [prototype 屬性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)