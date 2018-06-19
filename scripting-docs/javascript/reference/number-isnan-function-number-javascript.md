---
title: Number.isNaN 函式 （數字） (JavaScript) |Microsoft 文件
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c11abe2dd2fc70431800d31f4c44279a88cd75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639058"
---
# <a name="numberisnan-function-number-javascript"></a>Number.isNaN 函式 (數字) (JavaScript)
傳回布林值，表示值是否為保留的值 `NaN` (不是數字)。  
  
## <a name="syntax"></a>語法  
  
```  
Number.isNaN(numValue)   
```  
  
#### <a name="parameters"></a>參數  
 `numValue`  
 必要項。 針對 `NaN` 測試的值。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果此值轉換成 `Number` 類型是 `NaN`，否則為 `false`。  
  
## <a name="remarks"></a>備註  
 您通常使用這個方法測試從 `parseInt` 和 `parseFloat` 方法傳回的值。  
  
 `Number.isNaN` 以全域 `isNaN` 函式更正問題。 只有在與 `NaN` 比較之後，`Number.isNaN` 才會將其引數轉換為數字類型。 最後，如果且只有在傳入的引數值與 `NaN` 完全相同時，會傳回 `true`。 全域 `isNaN` 函式會在比較之前，將其引數轉換成數字類型，這會造成非數值傳回 `true`，而它們可能不會傳回 `Number.isNaN` 的 `true`。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用於**:[編號物件](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>範例  
  
```JavaScript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```