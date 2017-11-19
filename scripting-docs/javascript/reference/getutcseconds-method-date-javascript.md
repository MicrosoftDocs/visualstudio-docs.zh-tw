---
title: "getUTCSeconds 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC times, returning
- seconds method
- getUTCSeconds method
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f398145f8e31ed633bf3215de7d5a5ef669b7ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="getutcseconds-method-date-javascript"></a>getUTCSeconds 方法 (日期) (JavaScript)
取得的秒`Date`物件使用國際標準時間 (UTC)。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回一個整數，介於 0 到 59 之間。 時間少於一秒到目前的分鐘時，會傳回零。 如果`Date`已建立物件，而不指定的時間、 UTC 預設秒值為 0。  
  
## <a name="remarks"></a>備註  
 若要取得以本地時間的秒數，請使用`getSeconds`方法。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `getUTCSeconds` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getSeconds 方法 （日期）](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds 方法 （日期）](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)