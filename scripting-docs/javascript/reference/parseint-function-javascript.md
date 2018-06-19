---
title: parseInt 函式 (JavaScript) |Microsoft 文件
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
- parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639608"
---
# <a name="parseint-function-javascript"></a>parseInt 函式 (JavaScript)
將字串轉換成整數。  
  
## <a name="syntax"></a>語法  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>參數  
 `numString`  
 必要項。 要轉換的數字的字串。  
  
 `radix`  
 選擇項。 值介於 2 到指定的基底中數字的 36 `numString`。 如果未提供這個引數，以 '0x' 前置詞的字串視為十六進位。 所有其他字串視為十進位。  
  
## <a name="remarks"></a>備註  
 `parseInt`函式會傳回整數值等於中內含數字`numString`。 如果沒有前置詞的`numString`可以成功剖析為整數， `NaN` （不是數字） 會傳回。  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 您可以針對測試`NaN`使用`isNaN`函式。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[全域物件](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  從開始[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]、`parseInt`函式不會將前置詞為 '0' 成八進位的字串。 當您不使用`parseInt`函式，不過，以 '0' 前置詞的字串可以仍會解譯為 octals。 請參閱[資料型別](../../javascript/data-types-javascript.md)有關八進位整數。  
  
## <a name="see-also"></a>另請參閱  
 [isNaN 函式](../../javascript/reference/isnan-function-javascript.md)   
 [parseFloat 函式](../../javascript/reference/parsefloat-function-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)   
 [valueOf 方法 (Object)](../../javascript/reference/valueof-method-object-javascript.md)