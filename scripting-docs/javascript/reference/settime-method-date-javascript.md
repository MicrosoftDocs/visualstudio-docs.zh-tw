---
title: "setTime 方法 （日期） (JavaScript) |Microsoft 文件"
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
- setTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- SetTime method
- time method
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66b1fbf5d668330eb727e8bfc50ee9d11a28be3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="settime-method-date-javascript"></a>setTime 方法 (日期) (JavaScript)
設定中的日期和時間值`Date`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 *（毫秒)*  
 必要項。 數字的值，代表自 1970 GMT 年 1 月 1 日午夜起經過的毫秒數。  
  
## <a name="remarks"></a>備註  
 如果*毫秒*是負數，則表示變成 1970年以前的日期。 可用的日期範圍是從 1970 大約 285616 年。  
  
 設定的日期和時間與`setTime`方法都是獨立的時區。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `setTime` 方法。  
  
```JavaScript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getTime 方法 (Date)](../../javascript/reference/gettime-method-date-javascript.md)