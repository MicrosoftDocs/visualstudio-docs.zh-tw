---
title: getUTCMinutes 方法 （日期） (JavaScript) |Microsoft 文件
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
- getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636808"
---
# <a name="getutcminutes-method-date-javascript"></a>getUTCMinutes 方法 (日期) (JavaScript)
取得分鐘數`Date`物件使用國際標準時間 (UTC)。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回一個整數，介於 0 到 59 之間。 小於一分鐘小時之後，會傳回零。 如果`Date`已建立物件，而不指定的時間、 UTC 預設分鐘值為 0。 不過，在其他時區，它可能會不同。  
  
## <a name="remarks"></a>備註  
 若要取得儲存使用本地時間的分鐘數，請使用`getMinutes`方法。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `getUTCMinutes` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getMinutes 方法 （日期）](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes 方法 （日期）](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)