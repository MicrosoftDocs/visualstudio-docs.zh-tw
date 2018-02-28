---
title: "getTimezoneOffset 方法 （日期） (JavaScript) |Microsoft 文件"
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
- getTimeZoneOffset
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getTimezoneOffset method
- time zones [Visual Studio]
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e49a3c8b7060e6097300f8aaf99b2ef869833018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="gettimezoneoffset-method-date-javascript"></a>getTimezoneOffset 方法 (日期) (JavaScript)
取得本機電腦上的時間與國際標準時間 (UTC) 之間的差異以分鐘為單位。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回目前的電腦上的時間之間的分鐘數 (用戶端電腦或從伺服器指令碼的伺服器電腦在呼叫這個方法) 與 UTC。 如果目前電腦的當地時間是 UTC （例如，太平洋日光節約時間） 和負值背後，如果目前的電腦本機時間晚於 UTC （例如日本），它是正數。 如果 New York City 中的伺服器由用戶端在洛杉磯連絡年 12 月 1 日`getTimezoneOffset`傳回 480，如果用戶端或 300 上執行，如果在伺服器上執行。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `getTimezoneOffset` 方法。  
  
```JavaScript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getTime 方法 (Date)](../../javascript/reference/gettime-method-date-javascript.md)