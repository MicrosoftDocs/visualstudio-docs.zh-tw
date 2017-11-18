---
title: "位元 OR 指派運算子 (| =) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '|='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '|= operator'
- bitwise operators, OR operator
- OR operator
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ce9cadcf07906c9eba6749706620ae6293c2682
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-assignment-operator--javascript"></a>位元 OR 指派運算子 (|=) (JavaScript)
針對變數值和運算式的值執行位元 OR，然後將結果指派給此變數。  
  
## <a name="syntax"></a>語法  
  
```  
  
result |= expression  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何變數。  
  
 *運算式*  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 使用此運算子是完全如同指定：  
  
```JavaScript  
result = result | expression  
```  
  
 **&#124; =**運算子會查看值的二進位表示法*結果*和*運算式*，並在其上的位元 OR 運算。 這項作業的結果行為就像這樣：  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 任何一邊的運算式有一個數字 1，結果會是 1 在該數字。 否則，結果中包含在該數字 0。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [位元 OR 運算子 (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)