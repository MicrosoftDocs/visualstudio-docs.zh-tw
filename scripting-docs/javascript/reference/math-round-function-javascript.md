---
title: "Math.round 函式 (JavaScript) |Microsoft 文件"
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
- round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="mathround-function-javascript"></a>Math.round 函式 (JavaScript)
傳回所提供的數值運算式，四捨五入為最接近的整數。  
  
## <a name="syntax"></a>語法  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>備註  
 所需`number`引數是捨入至最接近的整數值。  
  
 為正數，如果數值的小數部分`number`是 0.5 或更多，傳回的值等於最小的整數大於`number`。 如果小數部分小於 0.5，傳回值的最大整數小於或等於`number`。  
  
 負數，如果小數部分正好-0.5，則傳回值是大於 1 的數字的最小整數。  
  
 例如，`Math.round(8.5)`傳回 9，但`Math.round(-8.5)`會傳回-8。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**: [Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [Math.random 函式](../../javascript/reference/math-random-function-javascript.md)