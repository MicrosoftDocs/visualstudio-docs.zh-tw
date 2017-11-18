---
title: "Math 物件 (JavaScript) |Microsoft 文件"
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
helpviewer_keywords: Math object
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f16fe4edf6a2a49db15d74abc8ebe6e53f955710
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="math-object-javascript"></a>Math 物件 (JavaScript)
提供基本數學功能和常數的內建物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
Math.[{property | method}]  
```  
  
## <a name="parameters"></a>參數  
 *屬性*  
 必要項。 其中一項的屬性名稱**數學**。 物件。  
  
 *方法*  
 必要項。 其中一個的方法名稱**數學**。 物件。  
  
## <a name="remarks"></a>備註  
 **數學**物件無法使用建立**新**運算子，並提供錯誤，如果您嘗試這樣做。 載入指令碼引擎時，引擎會建立該物件。 您隨時都能在指令碼中使用該物件的所有方法和屬性。  
  
## <a name="requirements"></a>需求  
 `Math` 物件已引入 [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]。  
  
<a name="js56jsobjmathprop"></a>   
## <a name="constants"></a>常數  
 下表列出 `Math` 物件的常數。  
  
|常數|說明|  
|--------------|-----------------|  
|[Math.E 常數](../../javascript/reference/math-constants-javascript.md)|數學常數 e。 這是歐拉數 (自然對數的底數)。|  
|[Math.LN2 常數](../../javascript/reference/math-constants-javascript.md)|2 的自然對數。|  
|[Math.LN10 常數](../../javascript/reference/math-constants-javascript.md)|10 的自然對數。|  
|[Math.LOG2E 常數](../../javascript/reference/math-constants-javascript.md)|e 的底數-2 對數。|  
|[Math.LOG10E 常數](../../javascript/reference/math-constants-javascript.md)|e 的底數-10 對數。|  
|[Math.PI 常數](../../javascript/reference/math-constants-javascript.md)|Pi。 這是圓形周長與其直徑的比例。|  
|[Math.SQRT1_2 常數](../../javascript/reference/math-constants-javascript.md)|0.5 的平方根，或等於 1 除以 2 的平方根。|  
|[Math.SQRT2 常數](../../javascript/reference/math-constants-javascript.md)|2 的平方根。|  
  
<a name="js56jsobjmathmeth"></a>   
## <a name="functions"></a>函式  
 下表列出 `Math` 物件的函式。  
  
|函式|說明|  
|--------------|-----------------|  
|[Math.abs 函式](../../javascript/reference/math-abs-function-javascript.md)|傳回一個數字的絕對值。|  
|[Math.acos 函式](../../javascript/reference/math-acos-function-javascript.md)|傳回一個數字的反餘弦值。|  
|[Math.acosh 函式](../../javascript/reference/math-acosh-function-javascript.md)|傳回數字的雙曲反餘弦 (或反雙曲餘弦)。|  
|[Math.asin 函式](../../javascript/reference/math-asin-function-javascript.md)|傳回一個數字的反正弦值。|  
|[Math.asinh 函式](../../javascript/reference/math-asinh-function-javascript.md)|傳回數字的反雙曲正弦。|  
|[Math.atan 函式](../../javascript/reference/math-atan-function-javascript.md)|傳回一個數字的反正切值。|  
|[Math.atan2 函式](../../javascript/reference/math-atan2-function-javascript.md)|傳回從 X 軸到以提供的 y 和 x 座標所呈現的點之角度 (弧度)。|  
|[Math.atanh 函式](../../javascript/reference/math-atanh-function-javascript.md)|傳回數字的反雙曲正切。|  
|[Math.ceil 函式](../../javascript/reference/math-ceil-function-javascript.md)|傳回大於或等於所提供數值運算式的最小整數。|  
|[Math.cos 函式](../../javascript/reference/math-cos-function-javascript.md)|傳回一個數字的餘弦值。|  
|[Math.cosh 函式](../../javascript/reference/math-cosh-function-javascript.md)|傳回數字的雙曲線餘弦。|  
|[Math.exp 函式](../../javascript/reference/math-exp-function-javascript.md)|傳回*e* （自然對數的基底） 自乘為乘冪。|  
|[Math.expm1 函式](../../javascript/reference/math-expm1-function-javascript.md)|傳回 e 減去 1 (自然對數的基數) 的乘冪。|  
|[Math.floor 函式](../../javascript/reference/math-floor-function-javascript.md)|傳回小於或等於所提供數值運算式的最大整數。|  
|[Math.hypot 函式](../../javascript/reference/math-hypot-function-javascript.md)|傳回引數平方總和的平方根。|  
|[Math.imul 函式](../../javascript/reference/math-imul-function-javascript.md)|傳回兩個數字的乘積，這兩個數字會被視為 32 位元的帶正負號整數。|  
|[Math.log 函式](../../javascript/reference/math-log-function-javascript.md)|傳回一個數字的自然對數。|  
|[Math.log1p 函式](../../javascript/reference/math-log1p-function-javascript.md)|傳回 1 + a 數字的自然對數。|  
|[Math.log10 函式](../../javascript/reference/math-log10-function-javascript.md)|傳回數字以 10 為底數的對數。|  
|[Math.log2 函式](../../javascript/reference/math-log2-function-javascript.md)|傳回數字以 2 為底數的對數。|  
|[Math.max 函式](../../javascript/reference/math-max-function-javascript.md)|傳回兩個所提供數值運算式中的較大者。|  
|[Math.min 函式](../../javascript/reference/math-min-function-javascript.md)|傳回兩個所提供數字中的較小者。|  
|[Math.pow 函式](../../javascript/reference/math-pow-function-javascript.md)|傳回基底運算式的指定次方值。|  
|[Math.random 函式](../../javascript/reference/math-random-function-javascript.md)|傳回 0 與 1 之間的虛擬隨機數。|  
|[Math.round 函式](../../javascript/reference/math-round-function-javascript.md)|傳回四捨五入為最近整數的指定數值運算式。|  
|[Math.sign 函式](../../javascript/reference/math-sign-function-javascript.md)|傳回數字的正負號，以指出數字為正數、負數或 0。|  
|[Math.sin 函式](../../javascript/reference/math-sin-function-javascript.md)|傳回一個數字的正弦值。|  
|[Math.sinh 函式](../../javascript/reference/math-sinh-function-javascript.md)|傳回數字的反雙曲正弦。|  
|[Math.sqrt 函式](../../javascript/reference/math-sqrt-function-javascript.md)|傳回一個數字的平方根。|  
|[Math.tan 函式](../../javascript/reference/math-tan-function-javascript.md)|傳回一個數字的正切值。|  
|[Math.tanh 函式](../../javascript/reference/math-tanh-function-javascript.md)|傳回數字的雙曲線正切。|  
|[Math.trunc 函式](../../javascript/reference/math-trunc-function-javascript.md)|傳回數字的整數部分，並移除任何小數位數。|  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 物件](../../javascript/reference/javascript-objects.md)   
 [Number 物件](../../javascript/reference/number-object-javascript.md)