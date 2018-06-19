---
title: 數字常數 (JavaScript) |Microsoft 文件
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
helpviewer_keywords:
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639198"
---
# <a name="number-constants-javascript"></a>Number 常數 (JavaScript)
下列數字常數是 `Number` 物件的屬性。  
  
## <a name="number-object-constants"></a>Number 物件常數  
 您不需要建立 `Number` 物件來存取這些常數。  
  
|常數|傳回的值|  
|--------------|--------------------|  
|`Number.EPSILON`|可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最小數字。 約等於 2.2204460492503130808472633361816E-16。|  
|`Number.MAX_SAFE_INTEGER`|可在 JavaScript 中安全表示的最大數字。 等於 9007199254740991。|  
|`Number.MAX_VALUE`|可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最大數字。 約等於 1.79E+308。|  
|`Number.MIN_SAFE_INTEGER`|可在 JavaScript 中安全表示的最小數字。 等於-9007199254740991。|  
|`Number.MIN_VALUE`|可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示，最接近零的數字。 約等於 5.00E-324。|  
|`Number.NaN`|不是數字的值。<br /><br /> 在相等比較中，`NaN` 不等於任何值，包括它自己。 若要測試一個值是否等於`NaN`，使用[isNaN 函式](../../javascript/reference/isnan-function-javascript.md)。|  
|`Number.NEGATIVE_INFINITY`|小於可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示之最大負數的值。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會將 `NEGATIVE_INFINITY` 值顯示為 `-infinity`。|  
|`Number.POSITIVE_INFINITY`|大於可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示之最大數字的值。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會將 `POSITIVE_INFINITY` 值顯示為 `infinity`。|  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 對於 `Number.EPSILON``Number.MAX_SAFE_INTEGER` 和 `Number.MIN_SAFE_INTEGER`：  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用於**:[編號物件](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [Math 常數](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript 常數](../../javascript/reference/javascript-constants.md)   
 [Infinity 常數](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN 常數](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN 函式](../../javascript/reference/isnan-function-javascript.md)