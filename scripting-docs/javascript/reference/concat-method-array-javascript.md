---
title: "concat 方法 （陣列） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-array-javascript"></a>concat 方法 (Array) (JavaScript)
結合兩個或多個陣列。  
  
## <a name="syntax"></a>語法  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>參數  
 `array1`  
 必要項。 `Array`會串連其他陣列物件。  
  
 `item1,. . ., itemN`  
 選擇項。 要加入結尾的其他項目`array1`。  
  
## <a name="remarks"></a>備註  
 `concat`方法會傳回`Array`物件，包含串連`array1`和任何其他提供項目。  
  
 要加入的項目 (*item1 itemN*) 陣列，依順序新增，從清單中的第一個項目開始。 如果其中一個項目是陣列，其內容加入至結尾`array1`。 如果陣列以外的任何項目，做為單一陣列元素會將它加入至陣列的結尾。  
  
 來源陣列的項目會複製到產生的陣列，如下所示：  
  
-   如果從任何串連到新陣列的陣列複製物件時，會繼續物件參考都指向相同物件。 新的陣列或原始陣列中的變更會導致其他變更。  
  
-   如果數字或字串的值加入至新的陣列，這個值會複製。 變更一個陣列中的值不會影響其他的值。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`concat`陣列搭配使用時的方法：  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [concat 方法 （字串）](../../javascript/reference/concat-method-string-javascript.md)   
 [join 方法 (Array)](../../javascript/reference/join-method-array-javascript.md)