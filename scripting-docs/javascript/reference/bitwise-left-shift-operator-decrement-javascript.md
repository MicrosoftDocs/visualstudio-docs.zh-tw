---
title: "位元左移運算子 (&lt;&lt;) (JavaScript) |Microsoft 文件"
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
- <<
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- << operator
- left shift operators
- << operator, about << operator
- bitwise operators, Left Shift operator
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d63fc50659695f518e581edbed67c009b36577f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-left-shift-operator-ltlt-javascript"></a>位元左移運算子 (&lt;&lt;) (JavaScript)
向左移位的位元的運算式。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = expression1 << expression2  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何變數。  
  
 *expression1*  
 任何運算式。  
  
 *expression2*  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 **<<** 運算子移位的位元*expression1*中指定的位元數字向左*expression2*。 例如:   
  
```JavaScript  
var temp  
temp = 14 << 2  
```  
  
 變數*temp*的值為 56，因為 14 (二進位為 00001110) 向左的兩個位元等於 56 (00111000)。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [左移設定運算子 (<\<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [位元右移運算子 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [不帶正負號的右移運算子 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)