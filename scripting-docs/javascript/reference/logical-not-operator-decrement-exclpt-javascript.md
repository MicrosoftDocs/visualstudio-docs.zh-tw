---
title: 邏輯 NOT 運算子 （！）(JavaScript) |Microsoft 文件
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
- '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638938"
---
# <a name="logical-not-operator--javascript"></a>邏輯 NOT 運算子 (!)(JavaScript)
在運算式上執行邏輯否定運算。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何變數。  
  
 *運算式*  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 下表將說明如何*結果*決定。  
  
|如果`expression`是|然後`result`是|  
|------------------------|----------------------|  
|True|False|  
|False|True|  
  
 所有一元運算子，例如 **！** 運算子會評估運算式，如下所示：  
  
-   如果套用到未定義或`null`運算式中，執行階段錯誤，就會引發。  
  
-   物件會轉換成字串。  
  
-   字串會盡可能轉換成數字。 如果沒有，就會引發執行階段錯誤。  
  
-   布林值視為數字 （0，如果為 false，1，如果為 true）。  
  
 運算子會套用至產生的數字。  
  
 如 **！** 運算子，如果*運算式*非零，*結果*為零。 如果*運算式*為零，*結果*為 1。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [位元 NOT 運算子 （~）](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)