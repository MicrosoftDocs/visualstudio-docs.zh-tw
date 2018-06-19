---
title: toGMTString 方法 （日期） (JavaScript) |Microsoft 文件
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
- toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640108"
---
# <a name="togmtstring-method-date-javascript"></a>toGMTString 方法 (日期) (JavaScript)
傳回將日期轉換成使用格林威治標準中央的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>備註  
 所需`dateObj`參考可以是任何`Date`物件。  
  
 `toGMTString`方法已過時，而且會提供回溯相容性才提供。 建議您改用`toUTCString`方法改為。  
  
 `toGMTString`方法會傳回`String`使用 GMT 慣例格式化包含日期的物件。 傳回值的格式如下所示:"05 Jan 1996 00:00:00 GMT"。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toUTCString 方法 (Date)](../../javascript/reference/toutcstring-method-date-javascript.md)