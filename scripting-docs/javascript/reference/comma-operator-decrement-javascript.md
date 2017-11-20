---
title: "逗號運算子 （，） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="comma-operator--javascript"></a>逗號運算子 (,) (JavaScript)
讓兩個運算式循序執行。  
  
## <a name="syntax"></a>語法  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>參數  
 `expression1`  
 任何運算式。  
  
 `expression2`  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 `,`運算子會使要由左到右的順序執行的運算式。 常見用途`,`運算子是中的遞增運算式`for`迴圈。 例如：  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 `for`陳述式允許在單一運算式結尾的每個迴圈執行。 `,`運算子可讓多個運算式會被視為單一運算式，因此這兩個變數可能會累加。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [陳述式](../../javascript/reference/for-statement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)