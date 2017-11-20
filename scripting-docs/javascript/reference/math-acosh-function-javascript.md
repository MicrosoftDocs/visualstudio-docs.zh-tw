---
title: "Math.acosh 函式 (JavaScript) |Microsoft 文件"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd75140dfcf3d9ac703c2aeadf68bea4da9e0dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="mathacosh-function-javascript"></a>Math.acosh 函式 (JavaScript)
傳回數字的雙曲反餘弦 (或反雙曲餘弦)。  
  
## <a name="syntax"></a>語法  
  
```  
Math.acosh(number)  
```  
  
#### <a name="parameters"></a>參數  
 所需要的 `number` 引數是數字運算式。  
  
## <a name="return-value"></a>傳回值  
 `number` 引數的反雙曲餘弦 (弧度)。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用 `acosh` 函式。  
  
```JavaScript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## <a name="remarks"></a>備註  
 **適用於**: [Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Math.acos 函式](../../javascript/reference/math-acos-function-javascript.md)   
 [Math.asin 函式](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 函式](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 函式](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 函式](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 函式](../../javascript/reference/math-tan-function-javascript.md)   
 [Math 物件](../../javascript/reference/math-object-javascript.md)