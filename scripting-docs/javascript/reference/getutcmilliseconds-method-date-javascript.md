---
title: getUTCMilliseconds 方法 （日期） (JavaScript) |Microsoft 文件
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
- getUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- UTC times, returning
- getUTCMilliseconds method
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fb7cf202c8511bec00c10dc5b8c23bd198d8700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636818"
---
# <a name="getutcmilliseconds-method-date-javascript"></a>getUTCMilliseconds 方法 (日期) (JavaScript)
取得的毫秒`Date`物件使用國際標準時間 (UTC)。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回毫秒值的範圍是從 0-999 之間。  
  
## <a name="remarks"></a>備註  
 若要取得以本地時間的毫秒數，請使用`getMilliseconds`方法。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `getUTCMilliseconds` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getMilliseconds 方法 （日期）](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds 方法 （日期）](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)