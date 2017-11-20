---
title: "slice 方法 （陣列） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-array-javascript"></a>slice 方法 (Array) (JavaScript)
傳回陣列的一個區段。  
  
## <a name="syntax"></a>語法  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 `Array` 物件。  
  
 `start`  
 必要項。 指定的部分開頭`arrayObj`。  
  
 `end`  
 選擇項。 結尾的指定部分`arrayObj`。  
  
## <a name="remarks"></a>備註  
 `slice`方法會傳回`Array`物件，其中包含的指定的部分`arrayObj`。  
  
 `slice`方法，但不是包含所指定的項目會複製`end`。 如果`start`是負數，則會被視為`length`  +  `start`，其中`length`是陣列的長度。 如果`end`是負數，則會被視為`length`  +  `end`其中`length`是陣列的長度。 如果省略 `end`，則會一直擷取到 `arrayObj` 的結尾。 如果`end`之前發生`start`，任何項目複製到新陣列。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用 `slice` 方法。 在第一個範例中，最後一個項目以外的所有`myArray`複製到`newArray`。 在第二個範例中，只有最後兩個元素的`myArray`複製到`newArray`。  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [slice 方法 （字串）](../../javascript/reference/slice-method-string-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)