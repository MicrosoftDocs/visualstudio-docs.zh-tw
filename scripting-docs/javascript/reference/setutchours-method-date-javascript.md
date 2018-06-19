---
title: setUTCHours 方法 （日期） (JavaScript) |Microsoft 文件
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
- setUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC times, setting
- setUTCHours method
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fe83735028f86d38ef270beac6c44dfa4caae7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641068"
---
# <a name="setutchours-method-date-javascript"></a>setUTCHours 方法 (日期) (JavaScript)
設定中的小時值`Date`物件使用國際標準時間 (UTC)。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 `numHours`  
 必要項。 數值等於小時值。  
  
 `numMin`  
 選擇項。 數值等於分鐘值。 如果必須提供`numSec`或`numMilli`可用。  
  
 `numSec`  
 選擇項。 數值等於秒數值。 如果必須提供`numMilli`使用引數。  
  
 `numMilli`  
 選擇項。 數值等於毫秒值。  
  
## <a name="remarks"></a>備註  
 所有**設定**接受選擇性引數的方法會使用對應的傳回值**取得**方法，如果您沒有指定選擇性引數。 例如，如果`numMin`未指定引數，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]從傳回的值會使用`getUTCMinutes`方法。  
  
 若要設定使用本地時間的小時值，請使用`setHours`方法。  
  
 如果引數的值大於它的範圍，或為負數，就會據以修改其他的儲存的值。 例如，如果預存的日期是"1996 年 1 月 5 日 00:00:00.00"和**setUTCHours(30)** 是呼叫，日期變更為"1996 年 1 月 6 日 06:00:00.00。 」  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `setUTCHours` 方法。  
  
```JavaScript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getHours 方法 （日期）](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours 方法 （日期）](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours 方法 (Date)](../../javascript/reference/sethours-method-date-javascript.md)