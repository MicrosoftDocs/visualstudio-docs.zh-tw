---
title: "setMilliseconds 方法 （日期） (JavaScript) |Microsoft 文件"
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
- setMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- setMilliseconds method
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0cd339e1352511312ef9a9abf9a7ff02955c986
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="setmilliseconds-method-date-javascript"></a>setMilliseconds 方法 (日期) (JavaScript)
設定毫秒值`Date`物件使用本地時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 `numMilli`  
 必要項。 數值等於毫秒值。  
  
## <a name="remarks"></a>備註  
 若要設定毫秒值使用國際標準時間 (UTC)，使用`setUTCMilliseconds`方法。  
  
 如果值`numMilli`大於 999 為負數，或儲存的數字的秒數 （和分鐘、 小時等等如有必要） 就會遞增適當的容量。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `setMilliseconds` 方法。  
  
```JavaScript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getMilliseconds 方法 （日期）](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds 方法 （日期）](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)