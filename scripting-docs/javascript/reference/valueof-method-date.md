---
title: "valueOf 方法 （日期） |Microsoft 文件"
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
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c5e6ea3c3e28d866f7cabf92dc97b81703b5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-date"></a>valueOf 方法 (日期)
傳回儲存的時間值以毫秒為單位，1970 年 1 月 1 日 UTC 午夜。  
  
## <a name="syntax"></a>語法  
  
```  
  
date.valueOf()  
```  
  
#### <a name="parameters"></a>參數  
 `date`物件是一個日期的任何執行個體。  
  
## <a name="return-value"></a>傳回值  
 以毫秒為單位，年 1 月 1，1970年午夜 UTC 儲存的時間值。 這是相同的值`getTime`。  
  
## <a name="example"></a>範例  
 下列範例說明使用`valueOf`日期的方法。  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]