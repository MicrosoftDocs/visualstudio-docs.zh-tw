---
title: 位元 OR 運算子 (|)(JavaScript) |Microsoft 文件
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
- '|'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, OR operator
- OR operator
- '| operator'
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a91c616c84b9d38154bf936f61fb856a4ebad0f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633748"
---
# <a name="bitwise-or-operator--javascript"></a>位元 OR 運算子 (|) (JavaScript)
針對兩個運算式執行位元 OR。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = expression1 | expression2  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何變數。  
  
 *expression1*  
 任何運算式。  
  
 *expression2*  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 **&#124;** 運算子會查看兩個運算式值的二進位表示法，並在其上的位元 OR 運算。 這項作業的結果行為，如下所示：  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 任何一邊的運算式有一個數字 1，結果將會有 1 在該數字。 否則，結果將在該數字必須是 0。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [位元 OR 指派運算子 (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)