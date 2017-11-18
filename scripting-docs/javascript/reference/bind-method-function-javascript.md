---
title: "bind 方法 （函式） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parameters [JavaScript], bind method
- arguments [JavaScript], bind method
- bind method [JavaScript]
- this keyword [JavaScript], bind method
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd7fc752df9bd41f8625ac2cb484486dfd19558d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="bind-method-function-javascript"></a>bind 方法 (函式) (JavaScript)
針對指定的函式，建立具有與原始函式相同主體的繫結函式。 在繫結函式中，`this` 物件會解析為傳入的物件。 繫結函式具有指定的初始參數。  
  
## <a name="syntax"></a>語法  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### <a name="parameters"></a>參數  
 `function`  
 必要項。 函式物件。  
  
 `thisArg`  
 必要項。 `this` 關鍵字可在新函式中參考的物件。  
  
 `arg1`[,`arg2`[,`argN`]]]  
 選擇項。 要傳遞給新函式的引數清單。  
  
## <a name="return-value"></a>傳回值  
 與 `function` 函式相同，但是 `thisArg` 物件和初始引數不同的新函式。  
  
## <a name="exceptions"></a>例外狀況  
 如果指定的 `function` 引數不是函式，就會擲回 `TypeError` 例外狀況。  
  
## <a name="example"></a>範例  
 下列程式碼將示範如何使用 `bind` 方法。  
  
```JavaScript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## <a name="example"></a>範例  
 在下列範例中，`thisArg` 物件與包含原始方法的物件不同。  
  
```JavaScript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## <a name="example"></a>範例  
 下列程式碼將示範如何使用 `arg1[,arg2[,argN]]]` 引數。 繫結函式會使用 `bind` 方法中指定的參數做為第一個和第二個參數。 呼叫繫結函式時指定的所有參數都會當做第三個、第四個 (依此類推) 參數使用。  
  
```JavaScript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [函式物件](../../javascript/reference/function-object-javascript.md)   
 [filter 方法 （陣列）](../../javascript/reference/filter-method-array-javascript.md)   
 [使用 bind 方法](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [Hilo JavaScript 範例應用程式 （Windows 市集）](http://hilojs.codeplex.com/SourceControl/latest)