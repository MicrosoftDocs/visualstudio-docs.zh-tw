---
title: "Date.UTC 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="dateutc-function-javascript"></a>Date.UTC 函式 (JavaScript)
傳回從 1970 年 1 月 1 日午夜之間的毫秒數國際標準時間 (UTC) （或 GMT） 和指定的日期。  
  
## <a name="syntax"></a>語法  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>參數  
 `year`  
 必要項。 需要跨世紀日期精確度指定完整的年份。 如果`year`介於 0 到 99 之間使用，然後`year`假設為 1900年 + `year`。  
  
 `month`  
 必要項。 介於 0 到 11 （一月至十二月） 的整數，表示月份。  
  
 `day`  
 必要項。 介於 1 到 31 之間的整數日期。  
  
 `hours`  
 選擇項。 如果必須提供`minutes`提供。 從 0 到 23 （午夜到下午 11 點） 的整數，指定在一小時。  
  
 `minutes`  
 選擇項。 如果必須提供`seconds`提供。 指定的整數從 0 到 59 分鐘的時間。  
  
 `seconds`  
 選擇項。 如果必須提供`milliseconds`提供。 指定的整數從 0 到 59 的秒數。  
  
 `ms`  
 選擇項。 從 0 到 999 的整數來指定毫秒數。  
  
## <a name="remarks"></a>備註  
 `Date.UTC`函式會傳回之間午夜、 UTC 1970 年 1 月 1 日和提供之日期的毫秒數。 這個傳回值可以用於`setTime`方法並在`Date`物件建構函式。 如果引數的值大於它的範圍，或為負數，就會據以修改其他的儲存的值。 例如，如果您指定 150 秒，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]重新該數字將定義為兩分鐘到 30 秒。  
  
 之間的差異`Date.UTC`函式和`Date`物件建構函式可接受的日期是`Date.UTC`函式會假設 UTC，而`Date`物件建構函式會假設本機時間。  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `Date.UTC` 函式：  
  
```JavaScript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [setTime 方法 (Date)](../../javascript/reference/settime-method-date-javascript.md)