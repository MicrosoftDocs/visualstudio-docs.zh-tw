---
title: "reduceRight 方法 （陣列） (JavaScript) |Microsoft 文件"
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
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="reduceright-method-array-javascript"></a>reduceRight 方法 (陣列) (JavaScript)
在陣列中，以遞減順序的所有項目會呼叫指定的回呼函式。 回呼函式的傳回值即為累加結果，並做為下一個呼叫的引數提供給回呼函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`array1`|必要項。 陣列物件。|  
|`callbackfn`|必要項。 接受最多四個引數的函式。 `reduceRight` 方法會針對陣列中的每個元素各呼叫 `callbackfn` 函式一次。|  
|`initialValue`|選擇項。 如果`initialValue`指定，它用來開始累積為初始值。 第一次呼叫`callbackfn`函式會提供此值做為引數，而不是陣列值。|  
  
## <a name="return-value"></a>傳回值  
 物件，包含從上次呼叫回呼函式為累加的結果。  
  
## <a name="exceptions"></a>例外狀況  
 A`TypeError`例外狀況時擲回其中一個的下列條件成立：  
  
-   `callbackfn`引數不是函式物件。  
  
-   此陣列中包含任何項目和`initialValue`未提供。  
  
## <a name="remarks"></a>備註  
 如果`initialValue`提供，則`reduceRight`方法呼叫`callbackfn`函式的陣列，以遞減的索引順序中的每個項目一次。 如果沒有`initialValue`提供，則`reduceRight`方法呼叫`callbackfn`上每個項目，第二個到最後一個元素，以遞減的索引順序開始函式。  
  
 回呼函式的傳回值依現狀`previousValue`在下次呼叫回呼函式的引數。 上次呼叫回呼函式的傳回值是傳回值的`reduceRight`方法。  
  
 對於陣列中遺漏的元素則不會呼叫回呼函式。  
  
 若要累積的結果，依照遞增索引順序，使用[reduce 方法 （陣列）](../../javascript/reference/reduce-method-array-javascript.md)。  
  
## <a name="callback-function-syntax"></a>回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 您可以使用最多四個參數宣告回呼函式。  
  
 下表列出回呼函式參數。  
  
|回呼引數|定義|  
|-----------------------|----------------|  
|`previousValue`|來自先前呼叫的回呼函式的值。 如果`initialValue`提供給`reduceRight`方法，`previousValue`是`initialValue`第一次呼叫函式。|  
|`currentValue`|目前的陣列元素的值。|  
|`currentIndex`|目前的陣列元素的數值索引。|  
|`array1`|包含元素的陣列物件。|  
  
## <a name="first-call-to-the-callback-function"></a>第一次呼叫的回呼函式  
 第一次呼叫的回呼函式時，當做引數提供的值取決於是否`reduceRight`方法有`initialValue`引數。  
  
 如果`initialValue`提供給`reduceRight`方法：  
  
-   `previousValue` 引數為 `initialValue`。  
  
-   `currentValue`引數是出現在陣列的最後一個元素的值。  
  
 如果`initialValue`未提供：  
  
-   `previousValue`引數是出現在陣列的最後一個元素的值。  
  
-   `currentValue`引數是出現在陣列的第二個到最後一個項目值。  
  
## <a name="modifying-the-array-object"></a>修改陣列物件  
 您可以透過回呼函式修改陣列物件。  
  
 下表描述在 `reduceRight` 方法啟動後修改陣列物件的結果。  
  
|`reduceRight` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|-----------------------------------------------------|------------------------------------------|  
|元素會在超出陣列原始長度的位置加入。|否。|  
|加入的元素會填補陣列中遺漏的元素。|是，如果該索引尚未傳遞至回呼函式的話。|  
|元素已變更。|是，如果該元素尚未傳遞至回呼函式的話。|  
|元素會從陣列中刪除。|否，除非該元素已傳遞至回呼函式。|  
  
## <a name="example"></a>範例  
 下列範例會將陣列值串連成字串，分隔的值與 「::"。 因為沒有初始值提供給`reduceRight`方法，回呼函式的第一個呼叫都有為 456`previousValue`引數和 123 as`currentValue`引數。  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## <a name="example"></a>範例  
 下列範例會尋找陣列項目的平方。 `reduceRight`會呼叫其初始值為 0。  
  
```JavaScript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## <a name="example"></a>範例  
 下列範例會取得的陣列，其值為 1 到 10 之間的這些項目。 提供給的初始值`reduceRight`方法是空陣列。  
  
```JavaScript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## <a name="example"></a>範例  
 `reduceRight` 方法可以套用至字串。 下列範例會示範如何使用這個方法來反轉字串中的字元。  
  
```JavaScript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [reduce 方法 (Array)](../../javascript/reference/reduce-method-array-javascript.md)