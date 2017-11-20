---
title: "Math.acos 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="mathacos-function-javascript"></a>Math.acos 函式 (JavaScript)
傳回數字的反餘弦 （或反餘弦）。  
  
## <a name="syntax"></a>語法  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>參數  
 所需要的 `number` 引數是數字運算式。  
  
## <a name="return-value"></a>傳回值  
 反餘弦的`number`引數，以弧度為單位。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用 `acos` 函式。  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>備註  
 **適用於**: [Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Math.asin 函式](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 函式](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 函式](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 函式](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 函式](../../javascript/reference/math-tan-function-javascript.md)   
 [Math 物件](../../javascript/reference/math-object-javascript.md)