---
title: "forEach 方法 （陣列） (JavaScript) |Microsoft 文件"
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
- forEach method [JavaScript]
- arrays [JavaScript], forEach method
- callback function, forEach method [JavaScript]
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec35c49e272ba50e26d3e4e7d892aa719a090d73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-array-javascript"></a>forEach 方法 (陣列) (JavaScript)
針對陣列中的每個元素執行指定的動作。  
  
## <a name="syntax"></a>語法  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`array1`|必要項。 陣列物件。|  
|`callbackfn`|必要項。 最多可以接受三個引數的函式。 `forEach` 會針對陣列中的每個元素各呼叫 `callbackfn` 函式一次。|  
|`thisArg`|選擇項。 `this` 關鍵字可在 `callbackfn` 函式中參考的物件。 如果省略 `thisArg`，則 `undefined` 就會做為 `this` 值使用。|  
  
## <a name="exceptions"></a>例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## <a name="remarks"></a>備註  
 `forEach` 方法會依照遞增索引順序，針對陣列中存在的每個元素各呼叫 `callbackfn` 函式一次。 對於陣列中遺漏的元素則不會呼叫回呼函式。  
  
 除了陣列物件之外，任何具有 `forEach` 屬性且具有數值索引屬性名稱的物件都可以使用 `length` 方法。  
  
## <a name="callback-function-syntax"></a>回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(value, index, array1)`  
  
 您最多可以使用三個參數宣告回呼函式。  
  
 回呼函式參數如下所示。  
  
|回呼引數|定義|  
|-----------------------|----------------|  
|`value`|陣列元素的值。|  
|`index`|陣列元素的數值索引。|  
|`array1`|包含元素的陣列物件。|  
  
## <a name="modifying-the-array-object"></a>修改陣列物件  
 `forEach` 方法不會直接修改原始陣列，但是回呼函式可能會修改它。 下表描述在 `forEach` 方法啟動後修改陣列物件的結果。  
  
|在 `forEach` 方法啟動後的狀況|元素是否會傳遞至回呼函式？|  
|---------------------------------------------|------------------------------------------|  
|元素會在超出陣列原始長度的位置加入。|否。|  
|加入的元素會填補陣列中遺漏的元素。|是，如果該索引尚未傳遞至回呼函式的話。|  
|元素已變更。|是，如果該元素尚未傳遞至回呼函式的話。|  
|元素會從陣列中刪除。|否，除非該元素已傳遞至回呼函式。|  
  
## <a name="example"></a>範例  
 下列範例將示範如何使用 `forEach` 方法。  
  
```JavaScript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## <a name="example"></a>範例  
 在下列範例中，`callbackfn` 引數包含回呼函式的程式碼。  
  
```JavaScript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## <a name="example"></a>範例  
 下列範例將示範如何使用 `thisArg` 引數指定可以透過 `this` 關鍵字參考的物件。  
  
```JavaScript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [filter 方法 （陣列）](../../javascript/reference/filter-method-array-javascript.md)   
 [map 方法 （陣列）](../../javascript/reference/map-method-array-javascript.md)   
 [some 方法 （陣列）](../../javascript/reference/some-method-array-javascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)   
 [Hilo JavaScript 範例應用程式 （Windows 市集）](http://hilojs.codeplex.com/SourceControl/latest)