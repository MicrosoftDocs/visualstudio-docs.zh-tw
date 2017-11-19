---
title: "Date.parse 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse function [JavaScript]
- Date.parse function [JavaScript]
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a73fda66ef24df17a5213a182c04667fc4dfabf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="dateparse-function-javascript"></a>Date.parse 函式 (JavaScript)
剖析字串，包含日期，並傳回該日期和從 1970 年 1 月 1 日午夜之間的毫秒數。  
  
## <a name="syntax"></a>語法  
  
```  
Date.parse(dateVal)   
```  
  
## <a name="remarks"></a>備註  
 所需`dateVal`引數是包含日期或 VT_DATE 值擷取自 ActiveX 物件或其他物件的其中一個的字串。 資訊的日期字串如`Date.parse`函式可剖析。 請參閱[日期和時間字串](../../javascript/date-and-time-strings-javascript.md)。  
  
 `Date.parse`函式會傳回整數值，代表自 1970 年 1 月 1 日午夜所提供的日期之間的毫秒數`dateVal`。  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `Date.parse` 函式：  
  
```JavaScript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## <a name="example"></a>範例  
 下列範例會傳回該日期與 1/1/1970年之間的差異。  
  
```JavaScript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [getDate 方法 (Date)](../../javascript/reference/getdate-method-date-javascript.md)