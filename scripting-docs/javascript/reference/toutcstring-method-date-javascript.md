---
title: toUTCString 方法 （日期） (JavaScript) |Microsoft 文件
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
- toUTCString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC dates, converting to strings
- toUTCString method
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd5efc43152c1af2dd467b73dce235e8fe52f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640738"
---
# <a name="toutcstring-method-date-javascript"></a>toUTCString 方法 (日期) (JavaScript)
傳回將日期轉換成使用國際標準時間 (UTC) 的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.toUTCString()   
```  
  
## <a name="remarks"></a>備註  
 所需`dateObj`參考可以是任何`Date`物件。  
  
 `toUTCString`方法會傳回`String`物件包含在一個方便使用 UTC 慣例來格式化的日期，輕鬆地讀取表單。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `toUTCString` 方法。  
  
```JavaScript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toGMTString 方法 (Date)](../../javascript/reference/togmtstring-method-date-javascript.md)