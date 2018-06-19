---
title: getMonth 方法 （日期） (JavaScript) |Microsoft 文件
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
- getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637388"
---
# <a name="getmonth-method-date-javascript"></a>getMonth 方法 (日期) (JavaScript)
取得使用本地時間的月份。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 `getMonth`方法會傳回整數，介於 0 （一月） 到 11 （12 月）。 如`Date`建構"1996 年 1 月 5 日 」`getMonth`傳回 0。  
  
## <a name="remarks"></a>備註  
 若要取得使用國際標準時間 (UTC) 的月份值，請使用`getUTCMonth`方法。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `getMonth` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getUTCMonth 方法 （日期）](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth 方法 （日期）](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth 方法 (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)