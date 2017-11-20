---
title: "Math 常數 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="math-constants-javascript"></a>Math 常數 (JavaScript)
數學常數傳回之內容的常數值`Math`物件。  
  
## <a name="math-object-constants"></a>Math 物件常數  
 下表列出是屬性的常數值[Math 物件](../../javascript/reference/math-object-javascript.md)。  
  
|常數|描述|近似數值|  
|--------------|-----------------|-----------------------|  
|`Math.E`|數學常數 e。 這是歐拉數 (自然對數的底數)。|2.718|  
|`Math.LN2`|2 的自然對數。|0.693|  
|`Math.LN10`|10 的自然對數。|2.302|  
|`Math.LOG2E`|e 的底數-2 對數。|1.443|  
|`Math.LOG10E`|e 的底數-10 對數。|0.434|  
|`Math.PI`|Pi。 這是圓形周長與其直徑的比例。|3.14159|  
|`Math.SQRT1_2`|0.5 的平方根，或等於 1 除以 2 的平方根。|0.707|  
|`Math.SQRT2`|2 的平方根。|1.414|  
  
## <a name="example"></a>範例  
 下列範例說明如何使用`Math.PI`常數。  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**: [Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [Number 常數](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript 常數](../../javascript/reference/javascript-constants.md)