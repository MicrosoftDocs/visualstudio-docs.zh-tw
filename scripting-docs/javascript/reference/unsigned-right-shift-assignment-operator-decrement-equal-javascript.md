---
title: "不帶正負號的右移指派運算子 (&gt;&gt;&gt;=) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>不帶正負號的右移指派運算子 (&gt;&gt;&gt;=) (JavaScript)
將變數值向右移位，移位的位元數由運算式中的值所指定，不保留正負號，然後將結果指派給此變數。  
  
## <a name="syntax"></a>語法  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何變數。  
  
 *運算式*  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 使用 >>> = 運算子是完全相同執行下列步驟：  
  
```JavaScript  
result = result >>> expression  
```  
  
 **>>>=** 運算子移位的位元*結果*向右旋轉中指定的位元數*運算式*。 從左邊會填入零。 捨棄移出右邊的數字。 例如:   
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 變數*temp*有初始值-14 (11111111 11111111 11111111 11110010 二的補數)。 當移位右側的兩個位元，則值會等於 1073741820 (二進位為 00111111 11111111 11111111 11111100)。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [不帶正負號的右移運算子 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [位元左移運算子 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [位元右移運算子 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)