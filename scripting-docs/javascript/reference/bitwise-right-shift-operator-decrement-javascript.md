---
title: 位元右移運算子 (&gt;&gt;) (JavaScript) |Microsoft 文件
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
- '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634268"
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>位元右移運算子 (&gt;&gt;) (JavaScript)
向右移位的位元的運算式中，保留正負號。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何變數。  
  
 *expression1*  
 任何運算式。  
  
 *expression2*  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 >> 運算子移位的位元*expression1*向右旋轉中指定的位元數*expression2*。 正負號位元的*expression1*用來填滿從左邊數字。 捨棄移出右邊的數字。 例如，下列程式碼評估之後, *temp*的值為-4:-14 （11110010 在二補數二進位） 向右移兩個位元等於-4 （11111100 在二補數二進位）。  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [位元左移運算子 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [右移設定運算子 (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [不帶正負號的右移運算子 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)