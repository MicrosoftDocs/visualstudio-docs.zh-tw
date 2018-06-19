---
title: every 方法 （陣列） (JavaScript) |Microsoft 文件
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
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637398"
---
# <a name="every-method-array-javascript"></a>every 方法 (陣列) (JavaScript)
判斷陣列的所有成員是否都符合指定的測試。  
  
## <a name="syntax"></a>語法  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`array1`|必要項。 陣列物件。|  
|`callbackfn`|必要項。 最多可以接受三個引數的函式。 `every`方法呼叫`callbackfn`函式中每個元素`array1`直到`callbackfn`傳回`false`，或直到陣列的結尾。|  
|`thisArg`|選擇項。 `this` 關鍵字可在 `callbackfn` 函式中參考的物件。 如果省略 `thisArg`，則 `undefined` 就會做為 `this` 值使用。|  
  
## <a name="return-value"></a>傳回值  
 `true`如果`callbackfn`函式會傳回`true`為所有陣列項目; 否則`false`。 如果陣列是沒有任何項目，`every`方法會傳回`true`。  
  
## <a name="exceptions"></a>例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## <a name="remarks"></a>備註  
 `every`方法呼叫`callbackfn`函式一次，每個陣列項目，依照遞增索引順序，直到`callbackfn`函式會傳回`false`。 如果項目，會導致`callbackfn`傳回`false`找到，`every`方法會立即傳回`false`。 否則，`every`方法會傳回`true`。  
  
 對於陣列中遺漏的元素則不會呼叫回呼函式。  
  
 除了陣列物件之外，任何具有 `every` 屬性且具有數值索引屬性名稱的物件都可以使用 `length` 方法。  
  
> [!NOTE]
>  您可以使用[某些方法 （陣列）](../../javascript/reference/some-method-array-javascript.md)來檢查是否回呼函式會傳回`true`任何的陣列項目。  
  
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
  
 下表描述在 `every` 方法啟動後修改陣列物件的結果。  
  
|`every` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|-----------------------------------------------|------------------------------------------|  
|元素會在超出陣列原始長度的位置加入。|否。|  
|加入的元素會填補陣列中遺漏的元素。|是，如果該索引尚未傳遞至回呼函式的話。|  
|元素已變更。|是，如果該元素尚未傳遞至回呼函式的話。|  
|元素會從陣列中刪除。|否，除非該元素已傳遞至回呼函式。|  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `every` 方法。  
  
```JavaScript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## <a name="example"></a>範例  
 下列範例將示範如何使用 `thisArg` 引數指定 `this` 關鍵字可參考的物件。  
  
```JavaScript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [some 方法 （陣列）](../../javascript/reference/some-method-array-javascript.md)   
 [filter 方法 （陣列）](../../javascript/reference/filter-method-array-javascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)