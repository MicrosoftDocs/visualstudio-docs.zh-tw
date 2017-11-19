---
title: "unshift 方法 （陣列） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unshift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: unshift method
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3f0d210514d04afa5cf467819a5e843925e1a68
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="unshift-method-array-javascript"></a>unshift 方法 (陣列) (JavaScript)
在陣列的開頭插入新項目。  
  
## <a name="syntax"></a>語法  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 `Array` 物件。  
  
 `item1, item2,. . ., itemN`  
 選擇項。 若要在開頭插入項目`Array`。  
  
## <a name="remarks"></a>備註  
 `unshift`方法插入項目開頭的陣列，以便顯示引數清單中出現的順序相同。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `unshift` 方法。  
  
```JavaScript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [shift 方法 (Array)](../../javascript/reference/shift-method-array-javascript.md)