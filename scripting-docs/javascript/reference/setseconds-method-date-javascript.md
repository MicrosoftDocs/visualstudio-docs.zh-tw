---
title: "setSeconds 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setSeconds method
- seconds method
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b8d545307f6aac3506310c868a2860a6159a106
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="setseconds-method-date-javascript"></a>setSeconds 方法 (日期) (JavaScript)
設定秒數值`Date`物件使用本地時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 *numSeconds*  
 必要項。 數值等於秒數值。  
  
 `numMilli`  
 選擇項。 數值等於毫秒值。  
  
## <a name="remarks"></a>備註  
 所有**設定**接受選擇性引數的方法會使用對應的傳回值**取得**方法，如果您沒有指定選擇性引數。 例如，如果`numMilli`未指定引數，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]從傳回的值會使用**getMilliseconds**方法。  
  
 若要設定使用國際標準時間 (UTC) 值的秒數，使用`setUTCSeconds`方法。  
  
 如果引數的值大於它的範圍，或為負數，就會據以修改其他的儲存的值。 例如，如果預存的日期"1996 年 1 月 5 日 00:00:00"和**setSeconds(150)**是呼叫，日期變更為"1996 年 1 月 5 日 00:02:30。 」  
  
 `setHours`方法可以用來設定小時、 分鐘、 秒和毫秒為單位。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `setSeconds` 方法。  
  
```JavaScript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getSeconds 方法 （日期）](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds 方法 （日期）](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)