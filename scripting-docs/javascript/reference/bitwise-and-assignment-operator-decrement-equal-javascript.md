---
title: "位元 AND 指派運算子 (&amp;=) (JavaScript) |Microsoft 文件"
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
- '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>位元 AND 指派運算子 (&amp;=) (JavaScript)
設定變數值的位元 AND 運算的結果及運算式的值。 變數和運算式會被視為 32 位元整數。  
  
## <a name="syntax"></a>語法  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>參數  
 `result`  
 任何變數。  
  
 `expression`  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 使用此運算子相當於指定：  
  
```JavaScript  
result = result & expression  
```  
  
 [位元 AND 運算子 (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)之值的二進位表示法會查看`result`和`expression`，並在其上的位元 AND 運算。 這項作業的輸出行為就像這樣：  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 如果兩個運算式有 1 的數字，結果中都有 1 該數字。 否則，結果中包含在該數字 0。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [位元 AND 運算子 (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)