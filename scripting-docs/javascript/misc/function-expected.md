---
title: 預期的函式 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: f177bf81a43c45dcff4cef3040c64425ed544057
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816965"
---
# <a name="function-expected"></a>必須是函式
可能是您嘗試在不是物件的物件上叫用其中一個函式**原型**方法 `Function` ，或是您在函式呼叫內容中使用了物件。 例如，下列程式碼會產生這個錯誤，因為**範例**不是函數。  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只在物件上呼叫函式**原型**方法 `Function` 。  
  
- 請確定您使用函式呼叫運算子 `()` 只呼叫函數。  
  
## <a name="see-also"></a>另請參閱  
 [Function 物件](../../javascript/reference/function-object-javascript.md)   
 [prototype 屬性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)