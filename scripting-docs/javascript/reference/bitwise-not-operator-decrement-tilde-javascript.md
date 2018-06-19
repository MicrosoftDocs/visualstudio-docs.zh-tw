---
title: 位元 NOT 運算子 （~） (JavaScript) |Microsoft 文件
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
- "~"
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634258"
---
# <a name="bitwise-not-operator--javascript"></a>位元 NOT 運算子 (~) (JavaScript)
針對運算式執行位元 NOT (否定) 運算。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何變數。  
  
 *運算式*  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 所有一元運算子，例如`~`運算子，評估運算式，如下所示：  
  
-   如果套用到未定義或`null`運算式中，執行階段錯誤，就會引發。  
  
-   物件會轉換成字串。  
  
-   字串會盡可能轉換成數字。 如果沒有，就會引發執行階段錯誤。  
  
-   布林值視為數字 （0，如果為 false，1，如果為 true）。  
  
 運算子會套用至產生的數字。  
  
 `~`運算子的運算式值的二進位表示法會查看，然後執行它的位元否定運算。  
  
 任何運算式中為 1 的數字會變成 0，結果中。 任何運算式中為 0 的數字會變成結果為 1。  
  
 下列範例說明使用的位元 NOT （~） 運算子。  
  
```  
var temp = ~5;  
```  
  
 產生的值是-6 下, 表所示。  
  
|運算式|二進位值 （二的補數）|十進位值|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [邏輯 NOT 運算子 （！）](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)