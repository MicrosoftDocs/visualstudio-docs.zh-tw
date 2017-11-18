---
title: "Math.max 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: max
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: max method
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf66164346f3802d92f8e0de82356df49bad5fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="mathmax-function-javascript"></a>Math.max 函式 (JavaScript)
傳回較大的一組提供的數值運算式。  
  
## <a name="syntax"></a>語法  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## <a name="remarks"></a>備註  
 選擇性`number1, number2, ..., numberN`引數是要評估的數值運算式。  
  
 如果未不提供任何引數，則傳回的值等於[Number.NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)。 如果任何引數為`NaN`，傳回值也是`NaN`。  
  
## <a name="example"></a>範例  
 下列程式碼會示範如何取得較大的兩個運算式。  
  
```JavaScript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Math.min 函式](../../javascript/reference/math-min-function-javascript.md)