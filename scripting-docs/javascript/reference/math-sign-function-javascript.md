---
title: "Math.sign 函式 (JavaScript) |Microsoft 文件"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cae32118f2265e02c67592facff8e49e8edd633
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="mathsign-function-javascript"></a>Math.sign 函式 (JavaScript)
傳回數字的正負號，以指出數字為正數、負數或 0。  
  
## <a name="syntax"></a>語法  
  
```  
Math.sign(number)  
```  
  
## <a name="remarks"></a>備註  
 所需之 `number` 引數是須有正負號的數值運算式。  
  
 傳回值可以是下列其中之一：  
  
-   `NaN`，如果 `number` 是 `NaN`。  
  
-   -0，如果`number`是 0。  
  
-   +0，如果 `number` 是 +0。  
  
-   -1，如果`number`為負數，-0。  
  
-   +1，如果 `number` 是正值，而且不是 +0。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]