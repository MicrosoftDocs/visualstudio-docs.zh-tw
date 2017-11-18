---
title: "Math.imul 函式 (JavaScript) |Microsoft 文件"
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57820d0926d574c75924f4eef6265ef7fa0766da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="mathimul-function-javascript"></a>Math.imul 函式 (JavaScript)
傳回兩個數字的乘積，這兩個數字會被視為 32 位元的帶正負號整數。  
  
## <a name="syntax"></a>語法  
  
```  
Math.imul(x, y);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 必要項。 第一個數字。  
  
 `y`  
 必要項。 第二個數字。  
  
## <a name="remarks"></a>備註  
 此函式用於像 Emscripten 和 Mandreel 的編譯器，它們實作整數乘法的方式與 JavaScript 不同。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 `Math.imul` 將數字相乘。  
  
```JavaScript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]