---
title: "splice 方法 （陣列） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="splice-method-array-javascript"></a>splice 方法 (陣列) (JavaScript)
移除陣列中的項目，並依需要在適當位置插入新項目，然後傳回被刪除的項目。  
  
## <a name="syntax"></a>語法  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 `Array` 物件。  
  
 `start`  
 必要項。 要從中開始移除項目陣列中以零為起始的位置。  
  
 `deleteCount`  
 必要項。 要移除的項目數目。  
  
 `item1, item2,. . ., itemN`  
 選擇項。 要取代的已刪除的項目陣列中插入項目。  
  
## <a name="remarks"></a>備註  
 `splice`方法會修改`arrayObj`藉由移除指定的項目數目，從位置`start`和插入新項目。 已刪除的項目會傳回為新`Array`物件。  
  
## <a name="example"></a>範例  
 下列程式碼將示範如何使用 `splice` 方法。  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [slice 方法 (陣列)](../../javascript/reference/slice-method-array-javascript.md)