---
title: "setFullYear 方法 （日期） (JavaScript) |Microsoft 文件"
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
- setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="setfullyear-method-date-javascript"></a>setFullYear 方法 (日期) (JavaScript)
設定年`Date`物件使用本地時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 `numYear`  
 必要項。 年數值。  
  
 `numMonth`  
 選擇項。 以零為起始的月份 (0 代表年 1 月 1，11 december) 數值。 如果必須指定`numDate`指定。  
  
 `numDate`  
 選擇項。 數值相等的月份天數。  
  
## <a name="remarks"></a>備註  
 所有**設定**接受選擇性引數的方法會使用對應的傳回值**取得**方法，如果您沒有指定選擇性引數。 例如，如果`numMonth`引數是選擇性的但未指定，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]從傳回的值會使用**getMonth**方法。  
  
 此外，如果引數的值大於其行事曆範圍，或為負數，日期會復原向前或向後，適當地。  
  
 若要設定使用國際標準時間 (UTC) 的年份，使用`setUTCFullYear`方法。  
  
 Date 物件支援的年份範圍是大約之前和之後 1970年 285616 年。  
  
## <a name="example"></a>範例  
 下列範例說明使用`setFullYear`方法：  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getFullYear 方法 （日期）](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 （日期）](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)