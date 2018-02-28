---
title: "setUTCMonth 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmonth-method-date-javascript"></a>setUTCMonth 方法 (日期) (JavaScript)
設定中的月份值`Date`物件使用國際標準時間 (UTC)。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 `numMonth`  
 必要項。 數值等於月份。 年 1 月的值為 0，並由左至右連續遵循其他月份值。  
  
 `dateVal`  
 選擇項。 數字的值，表示月份天數。 如果未提供，呼叫值`getUTCDate`使用方法。  
  
## <a name="remarks"></a>備註  
 若要設定使用本地時間的月份值，請使用`setMonth`方法。  
  
 如果值`numMonth`大於 11 （年 1 月是月份 0），或為負數，儲存的年份會以遞增或遞減適當。 例如，如果預存的日期是"1996 年 1 月 5 日 00:00:00.00"和**setUTCMonth(14)**是呼叫，日期變更為"1997 年 3 月 5 日 00:00:00.00。 」  
  
 **SetUTCFullYear**方法可以用來設定年、 月和月份天數。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `setUTCMonth` 方法。  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getMonth 方法 （日期）](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth 方法 （日期）](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth 方法 (Date)](../../javascript/reference/setmonth-method-date-javascript.md)