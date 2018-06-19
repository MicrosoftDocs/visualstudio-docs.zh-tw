---
title: getDate 方法 （日期） (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- getDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, returning day of the month
- getDate method
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfb3a8ad3ba433dc776f0831d1eac4787b8aea90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636788"
---
# <a name="getdate-method-date-javascript"></a>getDate 方法 (日期) (JavaScript)
取得一天的--月，使用本地時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getDate()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 1 到 31 之間的整數來表示日-的--月份。  
  
## <a name="remarks"></a>備註  
 若要取得一天的--月使用通用的國際標準時間 (UTC)，請使用`getUTCDate`方法。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `getDate` 方法。  
  
```JavaScript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getUTCDate 方法 （日期）](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate 方法 （日期）](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate 方法 (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)