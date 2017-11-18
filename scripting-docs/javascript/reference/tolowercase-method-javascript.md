---
title: "toLowerCase 方法 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLowerCase method
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7510e074c11cf3d3f63b965bcd6f14946dc5a16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="tolowercase-method-javascript"></a>toLowerCase 方法 (JavaScript)
將字串中的所有字母字元轉換成小寫。  
  
## <a name="syntax"></a>語法  
  
```  
  
      strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## <a name="remarks"></a>備註  
 `toLowerCase`方法有不會影響非字母字元。  
  
 下列範例示範的效果`toLowerCase`方法：  
  
```JavaScript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toLocaleLowerCase 方法 （字串）](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase 方法 (String)](../../javascript/reference/touppercase-method-string-javascript.md)