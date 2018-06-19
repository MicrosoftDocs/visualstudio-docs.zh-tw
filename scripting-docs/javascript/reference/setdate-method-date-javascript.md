---
title: setDate 方法 （日期） (JavaScript) |Microsoft 文件
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
- setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640308"
---
# <a name="setdate-method-date-javascript"></a>setDate 方法 (日期) (JavaScript)
設定的數字的月份日期值`Date`物件使用本地時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 `numDate`  
 必要項。 數值等於的月份天數。  
  
## <a name="remarks"></a>備註  
 若要設定使用國際標準時間 (UTC) 的月份日期值，請使用`setUTCDate`方法。  
  
 如果值`numDate`大於月份的天數，移轉到更新版本的月份和/或年份日期彙總數目。 例如，如果預存的日期是 1996 年 1 月 5 日和`setDate(32)`呼叫時，1996 年 2 月 1 日的日期變更。 如果`numDate`為負的數字、 日期復原回先前的月份和/或年份。 例如，如果預存的日期是 1996 年 1 月 5 日和`setDate(-32)`呼叫時，是在 1995 年 11 月 29 日的日期變更。  
  
 [SetFullYear 方法 （日期）](../../javascript/reference/setfullyear-method-date-javascript.md)可以用來設定年、 月和月份天數。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `setDate` 方法。  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getDate 方法 （日期）](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear 方法 （日期）](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth 方法 （日期）](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate 方法 (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)