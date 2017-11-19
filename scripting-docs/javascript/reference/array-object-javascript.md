---
title: "Array 物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Array
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- constructor property
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a48d0ab5bac9d532e8fe8e356f4ea4df9e377b02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="array-object-javascript"></a>Array 物件 (JavaScript)
為任何資料類型的陣列建立提供支援。  
  
## <a name="syntax"></a>語法  
  
```
arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 要對其指派 `Array` 物件的變數名稱。  
  
 `size`  
 選擇項。 陣列的大小。 由於陣列是以零起始，因此建立的項目將擁有從零到 `size` -1 的索引。  
  
 `element0,...,elementN`  
 選擇項。 要放置在陣列中的項目。 這會建立與陣列 *n*  + 1 個元素，和`length`的 *n*  + 1。 使用這個語法時必須提供多個項目。  
  
## <a name="remarks"></a>備註  
 建立陣列之後，您可以使用 [ ] 標記法存取陣列中的個別項目。 請注意，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的陣列是以零起始。  
  
```JavaScript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 您可以將不帶正負號的 32 位元整數傳遞至 `Array` 建構函式以指定陣列大小。 如果值為負數或不是整數，則會發生執行階段錯誤。 如果您執行下列程式碼，則應該會在主控台中看到這個錯誤。  
  
```JavaScript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 如果將單一值傳遞至 `Array` 建構函式而且該值不是數字，則 `length` 屬性會設定為 1，並且唯一元素的值會成為單一傳入的引數。  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 JavaScript 陣列是疏鬆陣列，也就是說，陣列中的元素不一定包含資料。 在 JavaScript 中，只有實際包含資料的項目才存在於陣列中， 這樣可減少陣列所使用的記憶體數量。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 下列清單中的某些成員是在後來的版本中才導入。 如需詳細資訊，請參閱[版本資訊](../../javascript/reference/javascript-version-information.md)或個別成員的文件集。  
  
## <a name="properties"></a>屬性  
 下表列出 `Array` 物件的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[constructor 屬性](../../javascript/reference/constructor-property-array.md)|指定用來建立陣列的函式。|  
|[length 屬性 (陣列)](../../javascript/reference/length-property-array-javascript.md)|傳回比陣列所定義最高項目多一的整數值。|  
|[prototype 屬性](../../javascript/reference/prototype-property-array.md)|傳回陣列原型的參考。|  
  
## <a name="functions"></a>函式  
 下表描述 `Array` 物件的函式。  
  
|函式|說明|  
|--------------|-----------------|  
|[Array.from 函式](../../javascript/reference/array-from-function-array-javascript.md)|從陣列形式或遞迴物件傳回陣列。|  
|[Array.isArray 函式](../../javascript/reference/array-isarray-function-javascript.md)|傳回布林值，表示物件是否為陣列。|  
|[Array.of 函式](../../javascript/reference/array-of-function-array-javascript.md)|從傳入的引數傳回陣列。|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>方法  
 下表列出 `Array` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[concat 方法 (陣列)](../../javascript/reference/concat-method-array-javascript.md)|傳回由兩個陣列所組合而成的新陣列。|  
|[entries 方法](../../javascript/reference/entries-method-array-javascript.md)|傳回包含陣列機碼或值組的迭代器。|  
|[every 方法](../../javascript/reference/every-method-array-javascript.md)|確認定義的回呼函式是否針對陣列中的所有項目傳回 `true`。|  
|[fill 方法](../../javascript/reference/fill-method-array-javascript.md)|以指定的值填入陣列。|  
|[filter 方法](../../javascript/reference/filter-method-array-javascript.md)|在陣列的每個項目上呼叫定義的回呼函式，並傳回值陣列，回呼函式會針對這些值傳回 `true`。|  
|[findIndex 方法](../../javascript/reference/findindex-method-array-javascript.md)|傳回第一個陣列項目的索引值，而此陣列項目符合回呼函式中所指定的測試準則。|  
|[forEach 方法](../../javascript/reference/foreach-method-array-javascript.md)|針對陣列中的每個項目呼叫定義的回呼函式。|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|傳回布林值，表示物件是否具有指定名稱的屬性。|  
|[indexOf 方法 (Array)](../../javascript/reference/indexof-method-array-javascript.md)|傳回陣列中值第一個出現位置的索引。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|傳回布林值，表示物件是否存在於另一個物件的原型鏈結中。|  
|[join 方法](../../javascript/reference/join-method-array-javascript.md)|傳回由陣列中所有項目串連在一起所組成的 `String` 物件。|  
|[keys 方法](../../javascript/reference/keys-method-array-javascript.md)|傳回包含陣列索引值的迭代器。|  
|[lastIndexOf 方法 (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|傳回陣列中所指定值最後一個出現位置的索引。|  
|[map 方法](../../javascript/reference/map-method-array-javascript.md)|在陣列中的每個項目上呼叫定義的回呼函式，並傳回包含結果的陣列。|  
|[pop 方法](../../javascript/reference/pop-method-array-javascript.md)|移除陣列的最後一個項目，然後將它傳回。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|傳回布林值，表示指定的屬性是否為物件的一部分，以及是否可以列舉。|  
|[push 方法](../../javascript/reference/push-method-array-javascript.md)|附加新項目到陣列中，並傳回陣列的新長度。|  
|[reduce 方法](../../javascript/reference/reduce-method-array-javascript.md)|藉由針對陣列的所有項目呼叫已定義的回呼函式，累加單一結果。 回呼函式的傳回值即為累加結果，並做為下一個呼叫的引數提供給回呼函式。|  
|[reduceRight 方法](../../javascript/reference/reduceright-method-array-javascript.md)|藉由針對陣列的所有項目依遞減順序呼叫已定義的回呼函式，累加單一結果。 回呼函式的傳回值即為累加結果，並做為下一個呼叫的引數提供給回呼函式。|  
|[reverse 方法](../../javascript/reference/reverse-method-javascript.md)|傳回項目反轉的 `Array` 物件。|  
|[shift 方法](../../javascript/reference/shift-method-array-javascript.md)|移除陣列的第一個項目，然後將它傳回。|  
|[slice 方法 (陣列)](../../javascript/reference/slice-method-array-javascript.md)|傳回陣列的一個區段。|  
|[some 方法](../../javascript/reference/some-method-array-javascript.md)|確認定義的回呼函式是否針對陣列中的任何項目傳回 `true`。|  
|[sort 方法](../../javascript/reference/sort-method-array-javascript.md)|傳回項目已經排序的 `Array` 物件。|  
|[splice 方法](../../javascript/reference/splice-method-array-javascript.md)|移除陣列中的項目，並依需要在適當位置插入新項目，然後傳回被刪除的項目。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-method-object-javascript.md)|傳回使用目前地區設定的字串。|  
|[toString 方法](../../javascript/reference/tostring-method-array.md)|傳回陣列的字串表示。|  
|[unshift 方法](../../javascript/reference/unshift-method-array-javascript.md)|在陣列的開頭插入新項目。|  
|[valueOf 方法](../../javascript/reference/valueof-method-array.md)|取得陣列的參考。|  
|[values 方法](../../javascript/reference/values-method-array-javascript.md)|傳回包含陣列值的迭代器。|  
  
## <a name="see-also"></a>另請參閱  
 [捲動、 移動和縮放範例應用程式](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)