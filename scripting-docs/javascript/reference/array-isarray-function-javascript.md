---
title: Array.isArray 函式 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isArray function [JavaScript]
- Array.isArray function [JavaScript]
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c31bdfe022cd41648117fc80c8df257e48e592ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633468"
---
# <a name="arrayisarray-function-javascript"></a>Array.isArray 函式 (JavaScript)
判斷某個物件是否為陣列。  
  
## <a name="syntax"></a>語法  
  
```  
Array.isArray(object)   
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 必要項。 要測試的物件。  
  
## <a name="return-value"></a>傳回值  
 如果 `object` 是陣列，則為 `true`，否則為 `false`。 如果 `object` 引數不是物件， 會傳回 `false`。  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `Array.isArray` 函式：  
  
```JavaScript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof 運算子](../../javascript/reference/typeof-operator-decrementjavascript.md)