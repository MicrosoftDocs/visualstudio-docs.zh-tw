---
title: "lastIndexOf 方法 （陣列） (JavaScript) |Microsoft 文件"
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
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-array-javascript"></a>lastIndexOf 方法 (Array) (JavaScript)
傳回陣列中所指定值最後一個出現位置的索引。  
  
## <a name="syntax"></a>語法  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`array1`|必要項。 要搜尋的陣列物件。|  
|`searchElement`|必要項。 要在中尋找值`array1`。|  
|`fromIndex`|選擇項。 陣列索引處開始搜尋。 如果`fromIndex`已省略，則搜尋開始的陣列中的最後一個索引。|  
  
## <a name="return-value"></a>傳回值  
 最後一個出現的索引`searchElement`中陣列，或是-1`searchElement`找不到。  
  
## <a name="remarks"></a>備註  
 `lastIndexOf`方法會搜尋指定的值的陣列。 方法會傳回第一個，則為-1 的索引，如果找不到指定的值。  
  
 搜尋就會發生以遞減的索引順序 （最後一個成員第一次）。 若要搜尋以遞增順序，請使用[indexOf 方法 （陣列）](../../javascript/reference/indexof-method-array-javascript.md)。  
  
 陣列項目會相較於`searchElement`嚴格等類似所做的比較值`===`運算子。 如需詳細資訊，請參閱[比較運算子](../../javascript/reference/comparison-operators-javascript.md)。  
  
 選擇性`fromIndex`引數會指定要開始搜尋的陣列索引。 如果`fromIndex`大於或等於陣列長度，則整體陣列中搜尋。 如果`fromIndex`是負數，搜尋會從陣列長度加上`fromIndex`。 如果計算的索引小於 0，則傳回-1。  
  
## <a name="example"></a>範例  
 下列範例說明使用`lastIndexOf`方法。  
  
```JavaScript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [indexOf 方法 （陣列）](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)