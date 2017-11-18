---
title: "Math.hypot 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a66c0b082356b8dde3f51f739c130378d694f3b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="mathhypot-function-javascript"></a>Math.hypot 函式 (JavaScript)
傳回引數平方總和的平方根。  
  
## <a name="syntax"></a>語法  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### <a name="parameters"></a>參數  
 `value1`  
 必要項。 第一個數字。  
  
 `value2`  
 選擇項。 第二個數字。  
  
 `values`  
 選擇項。 一個或多個數字。  
  
## <a name="remarks"></a>備註  
 如果有任何引數是 NaN，則函式會傳回 NaN。 如果未提供任何引數，則函式會傳回 0。  
  
## <a name="example"></a>範例  
 下列範例示範使用 `Math.hypot` 函式的範例。  
  
```JavaScript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]