---
title: "如果...else 陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ifelse-statement-javascript"></a>if...else 陳述式 (JavaScript)
根據運算式的值而定，有條件地執行陳述式群組。  
  
## <a name="syntax"></a>語法  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>參數  
 `condition1`  
 必要項。 Boolean 運算式。 如果`condition1`是`null`或`undefined`，`condition1`會被視為`false`。  
  
 `statement1`  
 選擇項。 如果要執行的陳述式`condition1`是**true**。 可以是複合陳述式。  
  
 `condition2`  
 要評估的條件。  
  
 `statement2`  
 選擇項。 如果要執行的陳述式`condition2`是`true`。 可以是複合陳述式。  
  
 `statement3`  
 如果兩個`condition1`和`condition2`是`false`，執行此陳述式。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用`if`， `if else`，和`else`。  
  
 來括住的最佳作法是`statement1`和`statement2`大括弧 （{}） 為了清楚起見，以及避免發生意外的錯誤。  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [條件 (三元) 運算子 (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)