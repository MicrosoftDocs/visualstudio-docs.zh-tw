---
title: "位元 XOR 指派運算子 (^ =) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ^=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ^= operator, about ^= operator
- assignment operators, bitwise [JavaScript]
- bitwise operators, XOR operator
- XOR operator
- ^= operator
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511ff5b3346bb2b04bf4c24cb3e0b715b2ccf4c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-assignment-operator--javascript"></a>位元 XOR 指派運算子 (^=) (JavaScript)
針對變數和運算式執行位元互斥 OR 運算，然後將結果指派給此變數。  
  
## <a name="syntax"></a>語法  
  
```  
  
result ^= expression  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何變數。  
  
 *運算式*  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 使用 **^=** 運算子是完全如同指定：  
  
```JavaScript  
result = result ^ expression  
```  
  
 **^=** 運算子會查看兩個運算式值的二進位表示法，並在其上的位元排除 OR 運算。 這項作業的結果行為，如下所示：  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 當只有一個，運算式有一個數字 1 時，結果會有該數字 1。 否則，結果中包含在該數字 0。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [位元 XOR 運算子 (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)