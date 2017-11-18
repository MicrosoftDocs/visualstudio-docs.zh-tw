---
title: "邏輯 OR 運算子 (|)(JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '||'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '|| operator'
- logical OR operator
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80c8e1bcae57e13642a0c77ae75c7c2aac58ace6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="logical-or-operator--javascript"></a>邏輯 OR 運算子 (||) (JavaScript)
針對兩個運算式執行邏輯分離。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = expression1 || expression2  
```  
  
## <a name="parameters"></a>參數  
 *結果*  
 任何變數。  
  
 *expression1*  
 任何運算式。  
  
 *expression2*  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 如果任一個或兩個運算式評估為**True**，*結果*是**True**。 下表將說明如何*結果*取決於：  
  
|如果`expression1`是|和`expression2`是|`result`是|  
|-------------------------|--------------------------|---------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 使用下列規則，將非布林值轉換成布林值：  
  
-   所有物件都會都視為，則為 true。  
  
-   如果且只有是空字串會視為 false。  
  
-   `null`和未定義會被視為 false。  
  
-   數字，如果為 false，而且只有當，它們是 0。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)