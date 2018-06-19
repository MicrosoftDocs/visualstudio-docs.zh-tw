---
title: Math.abs 函式 (JavaScript) |Microsoft 文件
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
- abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638368"
---
# <a name="mathabs-function-javascript"></a>Math.abs 函式 (JavaScript)
傳回數字 （而不考慮為正數或負數的值） 的絕對值。 例如，-5 的絕對值是 5 絕對值相同。  
  
## <a name="syntax"></a>語法  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>參數  
 所需`number`引數是數值運算式的絕對就需要這個值。  
  
## <a name="return-value"></a>傳回值  
 數值的絕對值`number`引數。  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `abs` 函式：  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**: [Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [Math 物件](../../javascript/reference/math-object-javascript.md)