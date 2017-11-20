---
title: "toTimeString 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="totimestring-method-date-javascript"></a>toTimeString 方法 (日期) (JavaScript)
傳回字串值的時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>備註  
 必要的 `objDate` 參考是 `Date` 物件。  
  
 `toTimeString`方法會傳回字串值，包含目前時區的時間。  
  
## <a name="example"></a>範例  
 在下列範例中，時間午夜 1970 年 1 月 1 日 UTC 後，會設定為 2000年毫秒，並接著寫出。  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [toDateString 方法 （日期）](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)