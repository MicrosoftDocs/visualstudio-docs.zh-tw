---
title: "map 方法 （陣列） (JavaScript) |Microsoft 文件"
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
- map method [JavaScript]
- arrays [JavaScript], map method
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 609d9c88000a7a30fe8edc03b52df032f7d19ba9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="map-method-array-javascript"></a>map 方法 (陣列) (JavaScript)
在陣列中的每個項目上呼叫定義的回呼函式，並傳回包含結果的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`array1`|必要項。 陣列物件。|  
|`callbackfn`|必要項。 最多可以接受三個引數的函式。 `map` 方法會針對陣列中的每個元素各呼叫 `callbackfn` 函式一次。|  
|`thisArg`|選擇項。 `this` 關鍵字可在 `callbackfn` 函式中參考的物件。 如果省略 `thisArg`，則 `undefined` 就會做為 `this` 值使用。|  
  
## <a name="return-value"></a>傳回值  
 新陣列，其中每個元素都是相關原始陣列元素的回呼函式傳回值。  
  
## <a name="exceptions"></a>例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## <a name="remarks"></a>備註  
 `map` 方法會依照遞增索引順序，針對陣列中的每個元素各呼叫 `callbackfn` 函式一次。 對於陣列中遺漏的元素則不會呼叫回呼函式。  
  
 除了陣列物件之外，任何具有 `map` 屬性且具有數值索引屬性名稱的物件都可以使用 `length` 方法。  
  
## <a name="callback-function-syntax"></a>回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(value, index, array1)`  
  
 您最多可以使用三個參數宣告回呼函式。  
  
 下表列出回呼函式參數。  
  
|回呼引數|定義|  
|-----------------------|----------------|  
|`value`|陣列元素的值。|  
|`index`|陣列元素的數值索引。|  
|`array1`|包含元素的陣列物件。|  
  
## <a name="modifying-the-array-object"></a>修改陣列物件  
 您可以透過回呼函式修改陣列物件。  
  
 下表描述在 `map` 方法啟動後修改陣列物件的結果。  
  
|`map` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|---------------------------------------------|------------------------------------------|  
|元素會在超出陣列原始長度的位置加入。|否。|  
|加入的元素會填補陣列中遺漏的元素。|是，如果該索引尚未傳遞至回呼函式的話。|  
|元素已變更。|是，如果該元素尚未傳遞至回呼函式的話。|  
|元素會從陣列中刪除。|否，除非該元素已傳遞至回呼函式。|  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `map` 方法。  
  
```JavaScript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## <a name="example"></a>範例  
 下列範例將示範如何使用 `thisArg` 引數指定 `this` 關鍵字可參考的物件。  
  
```JavaScript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## <a name="example"></a>範例  
 在下列範例中，內建的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 方法會當做回呼函式使用。  
  
```JavaScript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## <a name="example"></a>範例  
 `map` 方法可以套用至字串。 下列範例將說明這點。  
  
```JavaScript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)   
 [filter 方法 （陣列）](../../javascript/reference/filter-method-array-javascript.md)   
 [forEach 方法 （陣列）](../../javascript/reference/foreach-method-array-javascript.md)   
 [Hilo JavaScript 範例應用程式 （Windows 市集）](http://hilojs.codeplex.com/SourceControl/latest)