---
title: "條件 （三元） 運算子 (？:)(JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '?:'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional operators
- conditional (Ternary) operator
- ternary
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dc34b5c633cfc02219cb01061e1aaa017e0f7f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-ternary-operator--javascript"></a>條件 (三元) 運算子 (?:) (JavaScript)
根據條件傳回兩個運算式的其中一個。  
  
## <a name="syntax"></a>語法  
  
```  
  
test ? expression1 : expression2  
```  
  
## <a name="parameters"></a>參數  
 `test`  
 任何布林運算式。  
  
 `expression1`  
 如果 `test` 為 `true`，則傳回運算式。 可以是逗號運算子。  
  
 `expression2`  
 如果 `test` 為 `false`，則傳回運算式。 多個運算式可藉由逗號運算式連結。  
  
## <a name="remarks"></a>備註  
 `?:` 運算子可當做 `if...else` 陳述式的簡短表示方式。 在一些大型運算式中，若使用 `if...else` 陳述式會顯得很冗長，通常會使用這類簡短表示方式。 例如:   
  
```JavaScript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 此範例會建立字串，包含"Good evening。 」 如果它是下午 6 點後。 使用 `if...else` 陳述式的同等程式碼看起來會像這樣：  
  
```JavaScript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [如果...else 陳述式](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [指令碼愛用者組態 widget 範例應用程式](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)