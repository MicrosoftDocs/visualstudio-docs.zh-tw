---
title: "valueOf 方法 （陣列） |Microsoft 文件"
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
ms.assetid: b694fe65-1297-4580-8af2-406932c06454
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68dc5599a495df42629ec49f25e8f5344f67e3d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-array"></a>valueOf 方法 (陣列)
傳回指定物件的基本值。  
  
## <a name="syntax"></a>語法  
  
```  
  
array.valueOf()  
```  
  
#### <a name="parameters"></a>參數  
 這個方法沒有任何參數。  
  
## <a name="return-value"></a>傳回值  
 傳回陣列的執行個體。  
  
## <a name="remarks"></a>備註  
 在下列範例中，具現化的陣列物件是這個方法的傳回值相同。  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.valueOf();  
  
if (arr === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]