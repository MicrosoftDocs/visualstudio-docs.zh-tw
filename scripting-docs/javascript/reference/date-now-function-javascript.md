---
title: "Date.now 函式 (JavaScript) |Microsoft 文件"
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
- now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="datenow-function-javascript"></a>Date.now 函式 (JavaScript)
取得目前的日期和時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>傳回值  
 1970 年 1 月 1 日午夜與目前的日期和時間之間的毫秒數。  
  
## <a name="remarks"></a>備註  
 [GetTime 方法](../../javascript/reference/gettime-method-date-javascript.md)傳回之間的毫秒數 1970 年 1 月 1 日，並在指定的日期。  
  
 如需如何計算經過的時間和比較日期資訊，請參閱[計算日期和時間 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `now` 方法。  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>需求  
 不支援在已安裝的版本早於 Internet Explorer 9。 不過，支援在文件模式如下： Quirks、 Internet Explorer 6 標準、 Internet Explorer 7 標準、 Internet Explorer 8 標準、 Internet Explorer 9 標準、 Internet Explorer 10 標準。 此外也提供支援[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [getTime 方法 （日期）](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date 物件](../../javascript/reference/date-object-javascript.md)   
 [計算日期和時間 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)