---
title: valueOf 方法 （數字） |Microsoft 文件
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
ms.assetid: 0242a9ce-d41a-4c9b-af59-e8df32bbd913
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7918fb94673803e99d476d63fd814bce19bf9a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640358"
---
# <a name="valueof-method-number"></a>valueOf 方法 (數字)
傳回指定數目的基本值。  
  
## <a name="syntax"></a>語法  
  
```  
  
number.valueOf()  
```  
  
#### <a name="parameters"></a>參數  
 這個方法沒有任何參數。  
  
## <a name="return-value"></a>傳回值  
 傳回數字。  
  
## <a name="remarks"></a>備註  
 在下列範例中，具現化的數字物件是這個方法的傳回值相同。  
  
```JavaScript  
var num = 1234;  
var s = num.valueOf();  
  
if (num === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]