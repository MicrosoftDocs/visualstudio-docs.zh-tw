---
title: "toISOString 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="toisostring-method-date-javascript"></a>toISOString 方法 (日期) (JavaScript)
傳回 ISO 格式的日期字串值。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>傳回值  
 國際標準組織 (ISO) 格式的日期字串表示。  
  
## <a name="exceptions"></a>例外狀況  
 如果`objDate`不包含有效的日期，`RangeError`擲回例外狀況。  
  
## <a name="remarks"></a>備註  
 ISO 格式是 ISO 8601 格式的簡化。 如需詳細資訊，請參閱[日期和時間字串](../../javascript/date-and-time-strings-javascript.md)。  
  
 時區一律為 UTC，表示後置詞 Z 輸出中。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `toISOString` 方法。  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Date 物件](../../javascript/reference/date-object-javascript.md)   
 [日期和時間字串](../../javascript/date-and-time-strings-javascript.md)