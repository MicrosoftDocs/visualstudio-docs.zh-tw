---
title: "邏輯 AND 運算子 (&amp;&amp;) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="logical-and-operator-ampamp-javascript"></a>邏輯 AND 運算子 (&amp;&amp;) (JavaScript)
針對兩個運算式執行邏輯結合運算。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>參數  
 `result`  
 任何變數。  
  
 `expression1`  
 任何運算式。  
  
 `expression2`  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 如果 `expression1` 計算結果為 `false`，則 `result` 為 `expression1`。 否則，`result` 為 `expression2`。 因此，如果兩個運算元都是 true，則此作業會傳回 `true`，否則會傳回 `false`。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 使用下列規則，將非布林值轉換成布林值：  
  
-   所有物件都會視為 `true`。  
  
-   如果它們空白，則會將字串視為 `false`。  
  
-   `null` 和 `undefined` 會視為 `false`。  
  
-   如果它是零，則 Number 是 `false`。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)