---
title: setUTCDate 方法 （日期） (JavaScript) |Microsoft 文件
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
- setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640598"
---
# <a name="setutcdate-method-date-javascript"></a>setUTCDate 方法 (日期) (JavaScript)
設定每一天中月份`Date`物件使用國際標準時間 (UTC)。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 *numDate*  
 必要項。 數值等於的月份天數。  
  
## <a name="remarks"></a>備註  
 若要設定使用本地時間的月份天數，使用`setDate`方法。  
  
 如果值*numDate*大於儲存在該月份的天數**日期**物件或為負數，日期會設定為相等的日期*numDate*減號預存的月份天數。 例如，如果預存的日期是 1996 年 1 月 5 日和**setutcdate （32)** 呼叫時，1996 年 2 月 1 日的日期變更。 負數有類似的行為。  
  
 **SetUTCFullYear**方法可以用來設定年、 月和月份天數。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `setUTCDate` 方法。  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getDate 方法 （日期）](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate 方法 （日期）](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate 方法 (Date)](../../javascript/reference/setdate-method-date-javascript.md)