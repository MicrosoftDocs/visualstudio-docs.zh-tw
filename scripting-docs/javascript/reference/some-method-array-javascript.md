---
title: "some 方法 （陣列） (JavaScript) |Microsoft 文件"
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="some-method-array-javascript"></a>some 方法 (陣列) (JavaScript)
判斷是否會傳回指定的回呼函式`true`任何的陣列項目。  
  
## <a name="syntax"></a>語法  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`array1`|必要項。 陣列物件。|  
|`callbackfn`|必要項。 最多可以接受三個引數的函式。 `some`方法呼叫`callbackfn`函式中每個元素`array1`直到`callbackfn`傳回`true`，或直到陣列的結尾。|  
|`thisArg`|選擇項。 `this` 關鍵字可在 `callbackfn` 函式中參考的物件。 如果省略 `thisArg`，則 `undefined` 就會做為 `this` 值使用。|  
  
## <a name="return-value"></a>傳回值  
 `true`如果`callbackfn`函式會傳回`true`任何陣列項目; 否則`false`。  
  
## <a name="exceptions"></a>例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## <a name="remarks"></a>備註  
 `some`方法呼叫`callbackfn`函式中遞增索引順序，直到每一個陣列元素`callbackfn`函式會傳回`true`。 如果項目，會導致`callbackfn`傳回`true`找到，`some`方法會立即傳回`true`。 如果回呼不會傳回`true`上任何項目，`some`方法會傳回`false`。  
  
 對於陣列中遺漏的元素則不會呼叫回呼函式。  
  
 除了陣列物件之外，任何具有 `some` 屬性且具有數值索引屬性名稱的物件都可以使用 `length` 方法。  
  
> [!NOTE]
>  您可以使用[every 方法 （陣列）](../../javascript/reference/every-method-array-javascript.md)來檢查是否回呼函式會傳回`true`陣列的所有項目。  
  
## <a name="callback-function-syntax"></a>回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(value, index, array1)`  
  
 您可以宣告回呼函式具有多達三個參數。  
  
 下表列出回呼函式參數。  
  
|回呼參數|定義|  
|------------------------|----------------|  
|`value`|陣列元素的值。|  
|`index`|陣列元素的數值索引。|  
|`array1`|包含元素的陣列物件。|  
  
## <a name="modifying-the-array-object"></a>修改陣列物件  
 您可以透過回呼函式修改陣列物件。  
  
 下表描述在 `some` 方法啟動後修改陣列物件的結果。  
  
|`some` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|----------------------------------------------|------------------------------------------|  
|元素會在超出陣列原始長度的位置加入。|否。|  
|加入的元素會填補陣列中遺漏的元素。|是，如果該索引尚未傳遞至回呼函式的話。|  
|元素已變更。|是，如果該元素尚未傳遞至回呼函式的話。|  
|元素會從陣列中刪除。|否，除非該元素已傳遞至回呼函式。|  
  
## <a name="example"></a>範例  
 下列範例會使用`some`方法，以找出是否有任何項目陣列中為偶數。  
  
```JavaScript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`thisArg`參數，指定的物件`this`關鍵字可參考。 它會檢查任何數字陣列中所傳遞的物件所提供的範圍  
  
```JavaScript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [every 方法 （陣列）](../../javascript/reference/every-method-array-javascript.md)   
 [filter 方法 （陣列）](../../javascript/reference/filter-method-array-javascript.md)   
 [map 方法 (Array)](../../javascript/reference/map-method-array-javascript.md)