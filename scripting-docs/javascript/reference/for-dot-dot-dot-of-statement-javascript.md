---
title: for...in..陳述式 (JavaScript) |Microsoft 文件
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2373d319347f927304c32cb47856405a1d69a6b2
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454592"
---
# <a name="forof-statement-javascript"></a>for...of 陳述式 (JavaScript)
針對取自可迭代物件之迭代器的每個值，執行一或多個陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>參數  
 `variable`  
 必要。 可以是 `object` 之任何屬性值的變數。  
  
 `object`  
 必要。 可反覆執行的物件，例如`Array`， `Map`， `Set`，或該物件會實作[迭代器介面](../../javascript/advanced/iterators-and-generators-javascript.md)。  
  
 `statements`  
 選擇性。 要針對 `object` 的每個值所執行的一或多個陳述式。 可以是複合陳述式。  
  
## <a name="remarks"></a>備註  
 在迴圈每次反覆運算開始時，`variable` 的值就是 `object` 的下一個屬性值。  
  
## <a name="example"></a>範例  
 以下範例將示範如何對陣列使用 `for...of` 陳述式。  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>範例  
 以下範例將示範如何對 `Map` 物件使用 `for...of` 陳述式。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [for...in..陳述式中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [陳述式](../../javascript/reference/for-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)