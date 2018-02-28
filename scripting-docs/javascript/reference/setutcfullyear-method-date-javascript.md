---
title: "setUTCFullYear 方法 （日期） (JavaScript) |Microsoft 文件"
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
- setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="setutcfullyear-method-date-javascript"></a>setUTCFullYear 方法 (日期) (JavaScript)
設定中的年份值`Date`物件使用國際標準時間 (UTC)。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 `numYear`  
 必要項。 數值等於年份。  
  
 `numMonth`  
 選擇項。 數值等於月份。 年 1 月的值為 0，並由左至右連續遵循其他月份值。 如果必須提供*numDate*提供。  
  
 *numDate*  
 選擇項。 數值等於的月份天數。  
  
## <a name="remarks"></a>備註  
 所有**設定**接受選擇性引數的方法會使用對應的傳回值**取得**方法，如果您沒有指定選擇性引數。 例如，如果`numMonth`未指定引數，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]從傳回的值會使用`getUTCMonth`方法。  
  
 此外，如果引數的值較大，其範圍或負的數字，其他預存的值會跟著修改。  
  
 若要設定使用本地時間的年份，使用`setFullYear`方法。  
  
 支援的年份範圍`Date`物件是從 1970 大約 285616 年。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `setUTCFullYear` 方法。  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getFullYear 方法 （日期）](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 （日期）](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)