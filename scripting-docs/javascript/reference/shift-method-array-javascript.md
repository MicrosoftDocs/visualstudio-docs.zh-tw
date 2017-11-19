---
title: "shift 方法 （陣列） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: shift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: shift method
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664c3f764950b329cea8356f5b350ee917f0a60f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="shift-method-array-javascript"></a>shift 方法 (陣列) (JavaScript)
移除陣列的第一個項目，然後將它傳回。  
  
## <a name="syntax"></a>語法  
  
```  
  
arrayObj.shift( )  
```  
  
#### <a name="parameters"></a>參數  
 所需`arrayObj`參考是`Array`物件。  
  
## <a name="return-value"></a>傳回值  
 傳回從陣列中移除的項目。  
  
## <a name="remarks"></a>備註  
 在下列程式碼中，說明了如何使用 `shift` 方法。  
  
```JavaScript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [unshift 方法 (Array)](../../javascript/reference/unshift-method-array-javascript.md)