---
title: toString 方法 （日期） |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640248"
---
# <a name="tostring-method-date"></a>toString 方法 (日期)
傳回日期的字串表示。 字串的格式取決於地區設定。 美國地區英文 (en-我們)，如下所述：  
  
 *一週的日**月份**天**小時*:*分鐘*:*第二個* *時區**年*  
  
## <a name="syntax"></a>語法  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>參數  
 `date`  
 必要項。 要表示為字串的日期。  
  
## <a name="return-value"></a>傳回值  
 傳回日期的字串表示。  
  
## <a name="example"></a>範例  
 下列範例說明使用`toString`日期的方法。  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]