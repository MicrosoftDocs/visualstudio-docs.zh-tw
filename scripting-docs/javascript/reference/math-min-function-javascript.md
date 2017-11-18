---
title: "Math.min 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: min
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: min method
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb496cff65db11cf6c99d6a6e687f39e20ea857c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="mathmin-function-javascript"></a>Math.min 函式 (JavaScript)
傳回較小的一組數值運算式。  
  
## <a name="syntax"></a>語法  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## <a name="remarks"></a>備註  
 選擇性`number1, number2, ..., numberN`引數是要評估的數值運算式。  
  
 如果未不提供任何引數，則傳回的值等於[Number.POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)。 如果任何引數為`NaN`，傳回值也是`NaN`。  
  
## <a name="example"></a>範例  
 下列程式碼會示範如何取得較小的兩個運算式。  
  
```JavaScript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Math.max 函式](../../javascript/reference/math-max-function-javascript.md)