---
title: reduce 方法 （陣列） (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callback function, reduce method [JavaScript]
- arrays [JavaScript], reduce method
- reduce method [JavaScript]
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d99f92d90885f26b19392b476ee64ae17bd40aed
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="reduce-method-array-javascript"></a>reduce 方法 (陣列) (JavaScript)
陣列中的所有項目會呼叫指定的回呼函式。 回呼函式的傳回值即為累加結果，並做為下一個呼叫的引數提供給回呼函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`array1`|必要。 陣列物件。|  
|`callbackfn`|必要。 接受最多四個引數的函式。 `reduce` 方法會針對陣列中的每個元素各呼叫 `callbackfn` 函式一次。|  
|`initialValue`|選擇性。 如果`initialValue`指定，它用來開始累積為初始值。 第一次呼叫`callbackfn`函式會提供此值做為引數，而不是陣列值。|  
  
## <a name="return-value"></a>傳回值  
 從上次呼叫回呼函式為累加的結果。  
  
## <a name="exceptions"></a>例外狀況  
 A`TypeError`例外狀況時擲回其中一個的下列條件成立：  
  
-   `callbackfn`引數不是函式物件。  
  
-   此陣列中包含任何項目和`initialValue`未提供。  
  
## <a name="remarks"></a>備註  
 如果`initialValue`提供，則`reduce`方法呼叫`callbackfn`函式一次，每個項目出現在陣列中，依照遞增索引順序。 如果`initialValue`未提供，`reduce`方法呼叫`callbackfn`上每個項目，第二個元素開始函式。  
  
 回呼函式的傳回值依現狀`accumulator`在下次呼叫回呼函式的引數。 上次呼叫回呼函式的傳回值是傳回值的`reduce`方法。  
  
 對於陣列中遺漏的元素則不會呼叫回呼函式。  
  
> [!NOTE]
>  [ReduceRight 方法 （陣列）](../../javascript/reference/reduceright-method-array-javascript.md)處理遞減索引順序中的項目。  
  
## <a name="callback-function-syntax"></a>回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(accumulator, currentValue, currentIndex, array1)`  
  
 您可以使用最多四個參數宣告回呼函式。  
  
 下表列出回呼函式參數。  
  
|回呼引數|定義|  
|-----------------------|----------------|  
|`accumulator`|來自先前呼叫的回呼函式的值。 如果`initialValue`提供給`reduce`方法，`accumulator`是`initialValue`第一次呼叫函式。|  
|`currentValue`|目前的陣列元素的值。|  
|`currentIndex`|目前的陣列元素的數值索引。|  
|`array1`|包含元素的陣列物件。|  
  
## <a name="first-call-to-the-callback-function"></a>第一次呼叫的回呼函式  
 第一次呼叫的回呼函式時，當做引數提供的值取決於是否`reduce`方法有`initialValue`引數。  
  
 如果`initialValue`提供給 reduce 方法：  
  
-   `accumulator` 引數為 `initialValue`。  
  
-   `currentValue`引數是出現在陣列的第一個元素的值。  
  
 如果`initialValue`未提供：  
  
-   `accumulator`引數是出現在陣列的第一個元素的值。  
  
-   `currentValue`引數是出現在陣列的第二個元素的值。  
  
## <a name="modifying-the-array-object"></a>修改陣列物件  
 您可以透過回呼函式修改陣列物件。  
  
 下表描述在 `reduce` 方法啟動後修改陣列物件的結果。  
  
|`reduce` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|------------------------------------------------|------------------------------------------|  
|元素會在超出陣列原始長度的位置加入。|否。|  
|加入的元素會填補陣列中遺漏的元素。|是，如果該索引尚未傳遞至回呼函式的話。|  
|元素已變更。|是，如果該元素尚未傳遞至回呼函式的話。|  
|元素會從陣列中刪除。|否，除非該元素已傳遞至回呼函式。|  
  
## <a name="example"></a>範例  
 下列範例會將陣列值串連成字串，分隔的值與 「::"。 因為沒有初始值提供給`reduce`方法，回呼函式的第一個呼叫具有與"abc"`accumulator`引數，而"def"做為`currentValue`引數。  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (accumulator, currentValue) {  
    return accumulator + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## <a name="example"></a>範例  
 下列範例會將陣列的值之後已捨入。 `reduce`會呼叫其初始值為 0。  
  
```JavaScript  
// Define the callback function.  
function addRounded (accumulator, currentValue) {  
    return accumulator + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## <a name="example"></a>範例  
 下列範例會將陣列中的值。 `currentIndex`和`array1`回呼函式中使用參數。  
  
```JavaScript  
function addDigitValue(accumulator, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return accumulator + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## <a name="example"></a>範例  
 下列範例會取得陣列，其中包含只有在介於 1 到 10，另一個陣列中的值。 提供給的初始值`reduce`方法是空陣列。  
  
```JavaScript  
function Process(accumulatedArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = accumulatedArray.concat(currentValue);  
    else  
        nextArray = accumulatedArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is accumulatedArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [reduceRight 方法 (Array)](../../javascript/reference/reduceright-method-array-javascript.md)
