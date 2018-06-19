---
title: getSeconds 方法 （日期） (JavaScript) |Microsoft 文件
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
- getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636778"
---
# <a name="getseconds-method-date-javascript"></a>getSeconds 方法 (日期) (JavaScript)
取得的秒`Date`物件，使用本地時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回一個整數，介於 0 到 59 之間。 時間少於一秒到目前的分鐘時，會傳回零。 如果`Date`已建立物件，而不指定的時間、 預設的秒數的值為 0。  
  
## <a name="remarks"></a>備註  
 若要取得使用國際標準時間 (UTC) 值的秒數，使用`getUTCSeconds`方法。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `getSeconds` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getUTCSeconds 方法 （日期）](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds 方法 （日期）](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)