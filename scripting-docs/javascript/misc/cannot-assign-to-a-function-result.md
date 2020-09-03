---
title: 無法指派給函數結果 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 84ec3426c80da0578dda7cb99e9160b81e31ab87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817628"
---
# <a name="cannot-assign-to-a-function-result"></a>無法指派給函式結果
您已嘗試將值指派給函數結果。 您可以將函式的結果指派給變數，但不能當做變數使用。 如果您想要將新值指派給函數本身，請省略函式呼叫運算子)  (括弧。 下列範例示範產生此錯誤的情況。  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請勿使用函式呼叫結果的值做為您可以 *指派*的值。 不過，您可以將函式呼叫的結果指派 *給變數* 。  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- 或者，您可以將函式本身 (而不是其傳回值) 指派給變數。  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Function 物件](../../javascript/reference/function-object-javascript.md)   
 [撰寫 JavaScript 程式碼](../../javascript/writing-javascript-code.md)   
 [函式](../../javascript/functions-javascript.md)