---
title: "餘數運算子 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="remainder-operator-javascript"></a>餘數運算子 (JavaScript)
會將其中一個運算式的值，由另一個值，並傳回餘數。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>引數  
 `result`  
 任何變數。  
  
 `number1`  
 任何數值運算式。  
  
 `number2`  
 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 相除的餘數運算子`number1`由`number2`並傳回餘數做為`result`。 正負號`result`的正負號相同`number1`。 值`result`介於 0 和數值的絕對值`number2`。  
  
 下列程式碼會示範如何使用餘數運算子。  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
