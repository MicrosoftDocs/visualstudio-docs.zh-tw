---
title: 預期的函式 |Microsoft Docs
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
ms.openlocfilehash: 988ca00613d3dec4c55309fd77bc43705a6038ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576586"
---
# <a name="function-expected"></a>必須是函式
可能是您嘗試在不是 `Function` 物件的物件上叫用其中一個**函數原型**方法，或是在函式呼叫內容中使用了物件。 例如，下列程式碼會產生這個錯誤，因為**範例**不是函數。  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只在 `Function` 物件上呼叫**函數原型**方法。  
  
- 請確定您使用函式呼叫運算子 `()` 只呼叫函數。  
  
## <a name="see-also"></a>請參閱  
 [函數物件](../../javascript/reference/function-object-javascript.md)   
 [prototype 屬性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)