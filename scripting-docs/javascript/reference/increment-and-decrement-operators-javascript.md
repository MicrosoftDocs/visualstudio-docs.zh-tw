---
title: "遞增 （+ +） 和遞減 （-） 運算子 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- increment operators, syntax
- ++ operator
- ++ operator, about ++ operator
- decrement operators, syntax
- -- operator
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 806bd321bb1f81d585a6595b8cf2842571164921
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="increment--and-decrement----operators-javascript"></a>遞增 (++) 和遞減 (--) 運算子 (JavaScript)
遞增運算子，增減遞減運算子的其中一個變數的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## <a name="parameters"></a>參數  
 `result`  
 任何變數。  
  
 `variable`  
 任何變數。  
  
## <a name="remarks"></a>備註  
 運算子會出現在變數之前，如果運算式求值之前，會修改這個值。 運算子會出現在變數中，如果運算式評估之後，就是會修改這個值。  換句話說，提供`j = ++k;`的值`j`為原始值的`k`再加 1; 給予`j = k++;`的值`j`為原始值的`k`，它就會遞增之後其值指派給`j`.  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)