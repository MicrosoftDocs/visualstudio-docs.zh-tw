---
title: "getMinutes 方法 （日期） (JavaScript) |Microsoft 文件"
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
- getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="getminutes-method-date-javascript"></a>getMinutes 方法 (日期) (JavaScript)
取得分鐘數`Date`物件，使用本地時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回一個整數，介於 0 到 59 之間。 小於一分鐘小時之後，會傳回零。 如果`Date`已建立物件，而不指定的時間，根據預設，分鐘值為 0。  
  
## <a name="remarks"></a>備註  
 若要取得使用國際標準時間 (UTC) 的分鐘值，請使用`getUTCMinutes`方法。  
  
## <a name="example"></a>範例  
 下列範例會示範如何`getMinutes`方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getUTCMinutes 方法 （日期）](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes 方法 （日期）](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)