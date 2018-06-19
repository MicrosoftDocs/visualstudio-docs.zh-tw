---
title: isNaN 函式 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637618"
---
# <a name="isnan-function-javascript"></a>isNaN 函式 (JavaScript)
傳回布林值，表示值是否為保留的值 `NaN` (不是數字)。  
  
## <a name="syntax"></a>語法  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>傳回值  
 `true` 如果此值轉換成 `Number` 類型是 `NaN`，否則為 `false`。  
  
## <a name="remarks"></a>備註  
 所需`numValue`是針對所要測試的值`NaN`。  
  
 您通常使用這個方法測試從 `parseInt` 和 `parseFloat` 方法傳回的值。  
  
 或者，變數包含`NaN`或另一個值無法與其本身比較。 如果比較結果不相等，則`NaN`。 這是因為`NaN`是唯一的值不是自己本身。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[全域物件](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>範例  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>另請參閱  
 [isFinite 函式](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN 常數](../../javascript/reference/nan-constant-javascript.md)   
 [parseFloat 函式](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt 函式](../../javascript/reference/parseint-function-javascript.md)