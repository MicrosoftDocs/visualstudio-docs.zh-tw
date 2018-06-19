---
title: indexOf 方法 （陣列） (JavaScript) |Microsoft 文件
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
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637478"
---
# <a name="indexof-method-array-javascript"></a>indexOf 方法 (Array) (JavaScript)
傳回陣列中值第一個出現位置的索引。  
  
## <a name="syntax"></a>語法  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`array1`|必要項。 陣列物件。|  
|`searchElement`|必要項。 要在中尋找值`array1`。|  
|`fromIndex`|選擇項。 陣列索引處開始搜尋。 如果`fromIndex`已省略，位於索引 0 開始搜尋。|  
  
## <a name="return-value"></a>傳回值  
 第一個出現的索引`searchElement`中陣列，或是-1`searchElement`找不到。  
  
## <a name="remarks"></a>備註  
 `indexOf`方法會搜尋指定的值的陣列。 方法會傳回第一個，則為-1 的索引，如果找不到指定的值。  
  
 依照遞增索引順序，就會搜尋。  
  
 陣列項目會相較於`searchElement`值完全相等類似`===`運算子。 如需詳細資訊，請參閱[比較運算子](../../javascript/reference/comparison-operators-javascript.md)。  
  
 選擇性`fromIndex`引數會指定要開始搜尋的陣列索引。 如果`fromIndex`大於或等於陣列長度-1 會傳回。 如果`fromIndex`是負數，搜尋會從陣列長度加上`fromIndex`。  
  
## <a name="example"></a>範例  
 下列範例說明使用`indexOf`方法。  
  
```JavaScript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)