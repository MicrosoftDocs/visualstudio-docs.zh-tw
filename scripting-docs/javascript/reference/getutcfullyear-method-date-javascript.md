---
title: "getUTCFullYear 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getUTCFullYear method
- Date object
- UTCFullYear method
- dates, UTC
- UTC dates, returning
- Full Year method
- UTC dates, getting
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8268631a96eed1f61ef4ba908b78680c8522096
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="getutcfullyear-method-date-javascript"></a>getUTCFullYear 方法 (日期) (JavaScript)
取得使用國際標準時間 (UTC) 的年份。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回以四位數的年份。 指定為兩位數的年份`Date`建構函式或在`setFullYear`假設為二十一世紀，因此，假設"5/14/12"，`getUTCFullYear`傳回"1912"。  
  
## <a name="remarks"></a>備註  
 若要取得使用本地時間的年份，請使用`getFullYear`方法。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `getUTCFullYear` 方法。  
  
```JavaScript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getFullYear 方法 （日期）](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear 方法 （日期）](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)