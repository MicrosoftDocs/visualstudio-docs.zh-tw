---
title: "parseFloat 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="parsefloat-function-javascript"></a>parseFloat 函式 (JavaScript)
將字串轉換為浮點數。  
  
## <a name="syntax"></a>語法  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>備註  
 所需`numString`引數是字串，包含浮點數。  
  
 `parseFloat`函式會傳回數值等於中內含數字`numString`。 如果沒有前置詞的`numString`可以成功剖析為浮點數， `NaN` （不是數字） 會傳回。  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 您可以針對測試`NaN`使用`isNaN`函式。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[全域物件](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [isNaN 函式](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt 函式](../../javascript/reference/parseint-function-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)