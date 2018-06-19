---
title: Object.is 函式 (JavaScript) |Microsoft 文件
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d4c281fdafbfacb0b1f6061ef4a90bfac99234
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638698"
---
# <a name="objectis-function-javascript"></a>Object.is 函式 (JavaScript)
傳回值，這個值表示兩個值是否相同。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
Object.is(value1, value2)  
```  
  
#### <a name="parameters"></a>參數  
 `value1`  
 必要項。 要測試的第一個值。  
  
 `value2`  
 必要項。 要測試的第二個值。  
  
## <a name="return-value"></a>傳回值  
 如果值相同，則為 `true`，否則為 `false`。  
  
## <a name="remarks"></a>備註  
 與 == 運算子不同， `Object.is` 在測試值時不會強制變更任何類型。  
  
 `Object.is` 所套用的比較類似 === 運算子所套用的比較，差異在於 `Object.is` 將 `Number.isNaN` 視為與 `NaN` 相同的值。 它也將 +0 和 -0 視為不同的值。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]