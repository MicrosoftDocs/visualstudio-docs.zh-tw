---
title: 無法指派給函式結果 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38cf04b388eaea8ad85f0399978f914feb937c0a
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844009"
---
# <a name="cannot-assign-to-a-function-result"></a>無法指派給函式結果
您嘗試指派值給函式的結果。 函式的結果可以指派給變數，但它不能做為變數。 如果您想要將新的值指派給函式本身，省略括號 （函式呼叫運算子）。 下列範例示範用來產生這個錯誤的情況。  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請勿使用函式呼叫結果的值作為項目即可*指派給*。 您可以指派函式呼叫的結果*變數*雖然。  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   或者，您可以指派函式本身 （而非其傳回的值），此變數。  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [函式物件](../../javascript/reference/function-object-javascript.md)   
 [撰寫 JavaScript 程式碼](../../javascript/writing-javascript-code.md)   
 [函式](../../javascript/functions-javascript.md)