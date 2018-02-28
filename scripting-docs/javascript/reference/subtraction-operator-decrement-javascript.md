---
title: "減法運算子 （-） (JavaScript) |Microsoft 文件"
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
- '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="subtraction-operator---javascript"></a>減法運算子 (-) (JavaScript)
減去另一個運算式的值，或提供的單一運算式的一元否定運算。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何數值變數。  
  
 `number`  
 任何數值運算式。  
  
 `number1`  
 任何數值運算式。  
  
 `number2`  
 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 在語法 1  **-** 運算子是用來尋找兩個數字之間的差異的算術減法運算子。 在語法 2  **-** 運算子用於一元負運算子指出運算式的負值。  
  
 語法 2 中，所有的一元運算子與運算式進行評估，如下所示：  
  
-   如果套用到未定義或`null`運算式中，執行階段錯誤，就會引發。  
  
-   物件會轉換成字串。  
  
-   字串會盡可能轉換成數字。 如果沒有，就會引發執行階段錯誤。  
  
-   布林值視為數字 （0，如果為 false，1，如果為 true）。  
  
 運算子會套用至產生的數字。 在語法 2 中，如果產生的數字是零，*結果*等於產生的數字的正負號相反。 如果產生的數字為零，*結果*為零。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [減法指派運算子 （-）](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)