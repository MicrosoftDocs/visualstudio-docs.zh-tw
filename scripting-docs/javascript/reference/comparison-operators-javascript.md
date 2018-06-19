---
title: 比較運算子 (JavaScript) |Microsoft 文件
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
- Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634198"
---
# <a name="comparison-operators-javascript"></a>比較運算子 (JavaScript)
傳回表示比較結果的布林值。  
  
## <a name="syntax"></a>語法  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>參數  
 `expression1`  
 任何運算式。  
  
 `comparisonoperator`  
 任何比較運算子。  
  
 `expression2`  
 任何運算式。  
  
## <a name="remarks"></a>備註  
 比較字串時[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]會使用 Unicode 字元值的字串運算式。  
  
 下列程式碼說明不同的運算子的群組行為根據型別和值的方式`expression1`和`expression2`:  
  
 關係運算子： `<`， `>`， `<=`，`>=`  
  
-   嘗試轉換同時`expression1`和`expression2`為數字。  
  
-   如果這兩個運算式都是字串，請執行字串比較。  
  
-   如果任一個運算式是`NaN`，則傳回`false`。  
  
-   負零等於零的正數。  
  
-   負的無限值小於包括它自己的所有項目。  
  
-   正無限值大於包括它自己的所有項目。  
  
 等號比較運算子： `==`，`!=`  
  
-   如果兩個運算式的類型不同，則會嘗試將它們轉換成字串、 數字或布林值。  
  
-   `NaN`不等於任何包括它自己的項目。  
  
-   負零等於零的正數。  
  
-   `null`等於兩者`null`和`undefined`。  
  
-   值會被視為相等，如果它們是完全相同的字串、 數字相等的數字、 相同的物件、 相同的布林值，或 (如果不同類型) 會強制轉成其中一種情況。  
  
-   其他所有的比較會被視為不相等。  
  
 識別運算子： `===`，`!==`  
  
 這些運算子的行為相同的等號比較運算子，不同之處在於，會執行任何類型轉換。 如果這兩個運算式的類型不相同，這些運算式一律會傳回`false`。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)