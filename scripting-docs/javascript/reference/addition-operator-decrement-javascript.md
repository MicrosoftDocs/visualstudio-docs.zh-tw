---
title: "加法運算子 （+） (JavaScript) |Microsoft 文件"
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
- +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="addition-operator--javascript"></a>加法運算子 (+) (JavaScript)
將一個數值運算式的值加入至另一個，或串連兩個字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>參數  
 `result`  
 任何變數。  
  
 `expression1`  
 任何運算式。  
  
 `expression2`  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 兩個運算式的型別決定的行為 **+** 運算子。  
  
|如果|然後|  
|--------|----------|  
|這兩個運算式都是數值或布林值|新增|  
|這兩個運算式都是字串|串連|  
|一個運算式為數值，另一個是字串|串連|  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [加法指派運算子 （+ =）](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)