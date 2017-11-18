---
title: "getHours 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="gethours-method-date-javascript"></a>getHours 方法 (日期) (JavaScript)
取得使用當地時間日期的小時。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 介於 0 到 23 之間，表示從午夜開始的小時數的整數。 如果時間 1:00:00 之前，會傳回零。 如果`Date`已建立物件，而不指定的時間，根據預設，在一小時為 0。  
  
## <a name="remarks"></a>備註  
 若要取得使用國際標準時間 (UTC) 的小時值，請使用`getUTCHours`方法。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `getHours` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getUTCHours 方法 （日期）](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours 方法 （日期）](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours 方法 (Date)](../../javascript/reference/setutchours-method-date-javascript.md)