---
title: "Math.clz32 函式 (JavaScript) |Microsoft 文件"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511f407acc327a32ed6c53c12283503e20b514fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="mathclz32-function-javascript"></a>Math.clz32 函式 (JavaScript)
傳回數字之 32 位元二進位表示法中的前置零位元數。  
  
## <a name="syntax"></a>語法  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## <a name="remarks"></a>備註  
 如果 `number` 是 0，則結果會是 32。 如果32 位元二進位編碼的最高有效位元 `number` 為 1，結果將會是 0。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用於**: [Math 物件](../../javascript/reference/math-object-javascript.md)