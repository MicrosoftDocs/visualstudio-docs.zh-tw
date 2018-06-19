---
title: Number 物件 (JavaScript) |Microsoft 文件
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
- Number_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number object
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cbe58fdc9673a8fffe35b8b15d7edbf86ffa655
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641668"
---
# <a name="number-object-javascript"></a>Number 物件 (JavaScript)
代表任何種類數字的物件。 所有 JavaScript 數字都是 64 位元浮點數。  
  
## <a name="syntax"></a>語法  
  
```  
  
numObj = new Number(value)  
```  
  
## <a name="parameters"></a>參數  
 `numObj`  
 必要項。 要對其指派 `Number` 物件的變數名稱。  
  
 `value`  
 必要項。 數值。  
  
## <a name="remarks"></a>備註  
 將變數設為數值時 (例如 `var num = 255.336;`)，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會建立 `Number` 物件。 很少需要明確地建立 `Number` 物件。  
  
 除了繼承自 `Object` 的屬性和方法之外，`Number` 物件還有它自己的屬性和方法。 在特定情況下，數字會轉換成字串，例如，加入數字或是串連數字與字串時，以及透過 `toString` 方法。 如需詳細資訊，請參閱[加法運算子 （+）](../../javascript/reference/addition-operator-decrement-javascript.md)。  
  
 JavaScript 具有數個數字常數。 如需完整清單，請參閱[數字常數](../../javascript/reference/number-constants-javascript.md)。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="properties"></a>屬性  
 下表列出 `Number` 物件的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[constructor 屬性](../../javascript/reference/constructor-property-object-javascript.md)|指定用來建立物件的函式。|  
|[prototype 屬性](../../javascript/reference/prototype-property-object-javascript.md)|傳回物件類別的原型參考。|  
  
## <a name="functions"></a>函式  
 下表列出的函式`Number`物件。  
  
|函式|說明|  
|--------------|-----------------|  
|[Number.isFinite 函式](../../javascript/reference/number-isfinite-function-number-javascript.md)|傳回布林值，表示值是否為有限。|  
|[Number.isInteger 函式](../../javascript/reference/number-isinteger-function-number-javascript.md)|傳回布林值，表示值是否為整數。|  
|[Number.isNaN 函式](../../javascript/reference/number-isnan-function-number-javascript.md)|傳回布林值，表示值是否為保留的值 `NaN` (不是數字)。|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|傳回布林值，表示是否可以在 JavaScript 中安全地表示值。|  
  
## <a name="methods"></a>方法  
 下表列出的方法`Number`物件。  
  
|方法|說明|  
|------------|-----------------|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|傳回布林值，表示物件是否具有指定名稱的屬性。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|傳回布林值，表示物件是否存在於另一個物件的原型階層。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|傳回布林值，表示指定的屬性是否為物件的一部分，以及是否可以列舉。|  
|[toExponential 方法](../../javascript/reference/toexponential-method-number-javascript.md)|傳回包含以指數標記法表示之數字的字串。|  
|[toFixed 方法](../../javascript/reference/tofixed-method-number-javascript.md)|傳回以固定點標記法表示之數字的字串。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-number.md)|傳回依據目前的地區設定轉換成字串的物件。|  
|[toPrecision 方法](../../javascript/reference/toprecision-method-number-javascript.md)|傳回包含以指數或固定點標記法表示以及含有指定位數的字串。|  
|[toString 方法](../../javascript/reference/tostring-method-object-javascript.md)|傳回物件的字串表示。|  
|[valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)|傳回指定物件的基本值。|  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 物件](../../javascript/reference/javascript-objects.md)   
 [Math 物件](../../javascript/reference/math-object-javascript.md)   
 [new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)