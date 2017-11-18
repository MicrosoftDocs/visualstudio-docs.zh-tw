---
title: "setMonth 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="setmonth-method-date-javascript"></a>setMonth 方法 (日期) (JavaScript)
設定中的月份值`Date`物件使用本地時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 `numMonth`  
 必要項。 數值等於月份。 年 1 月的值為 0，並由左至右連續遵循其他月份值。  
  
 `dateVal`  
 選擇項。 數字的值，表示月份天數。 如果未提供此值，呼叫值`getDate`使用方法。  
  
## <a name="remarks"></a>備註  
 若要設定月份值使用國際標準時間 (UTC)，使用`setUTCMonth`方法。  
  
 如果值`numMonth`大於 11 （年 1 月是月份 0） 或負數，據此修改儲存的年份。 例如，如果預存的日期是"1996 年 1 月 5 日 」 和**setMonth(14)**是呼叫，日期變更為"3 月 5，1997。 」  
  
 **SetFullYear**方法可以用來設定年、 月和月份天數。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `setMonth` 方法。  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getMonth 方法 （日期）](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth 方法 （日期）](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth 方法 (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)