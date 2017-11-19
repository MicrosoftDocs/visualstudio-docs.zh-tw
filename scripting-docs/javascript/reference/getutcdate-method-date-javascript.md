---
title: "getUTCDate 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, UTC
- UTC dates, returning
- getUTCDate method
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4c38244e989027139329ae6aab762fd9fbabb3a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="getutcdate-method-date-javascript"></a>getUTCDate 方法 (日期) (JavaScript)
取得一天的--月，使用國際標準時間 (UTC)。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回 1 到 31，代表天的--月之間的整數。  
  
## <a name="remarks"></a>備註  
 若要取得使用本地時間的月份天數，請使用`getDate`方法。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `getUTCDate` 方法。  
  
```JavaScript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getDate 方法 （日期）](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate 方法 （日期）](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate 方法 (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)