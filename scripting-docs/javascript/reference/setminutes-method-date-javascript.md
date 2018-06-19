---
title: setMinutes 方法 （日期） (JavaScript) |Microsoft 文件
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
- setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641188"
---
# <a name="setminutes-method-date-javascript"></a>setMinutes 方法 (日期) (JavaScript)
設定分鐘值**日期**物件使用本地時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 `numMinutes`  
 必要項。 數值等於分鐘值。 如果任一下列引數使用，必須提供。  
  
 *numSeconds*  
 選擇項。 數值等於秒數值。 如果必須提供`numMilli`使用引數。  
  
 `numMilli`  
 選擇項。 數值等於毫秒值。  
  
## <a name="remarks"></a>備註  
 所有**設定**接受選擇性引數的方法會使用對應的傳回值**取得**方法，如果您沒有指定選擇性引數。 例如，如果*numSeconds*未指定，引數[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]從傳回的值會使用`getSeconds`方法。  
  
 若要設定使用國際標準時間 (UTC) 的分鐘值，請使用`setUTCMinutes`方法。  
  
 如果引數的值大於它的範圍，或為負數，就會據以修改其他的儲存的值。 例如，如果預存的日期"1996 年 1 月 5 日 00:00:00"和**setMinutes(90)** 是呼叫，日期變更為"1996 年 1 月 5 日 01:30:00。 」 負數有類似的行為。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `setMinutes` 方法。  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getMinutes 方法 （日期）](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes 方法 （日期）](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)