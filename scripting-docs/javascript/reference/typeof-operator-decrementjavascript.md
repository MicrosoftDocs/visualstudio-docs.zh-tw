---
title: "typeof 運算子 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c79c69e6c447b14e61fa67ccb8600d5d83bebd2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="typeof-operator-javascript"></a>typeof 運算子 (JavaScript)
傳回可識別運算式之資料類型的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>備註  
 *運算式*引數是任何類型資訊所要搜尋的運算式。  
  
 `typeof`運算子會傳回做為字串的類型資訊。 有六個可能值的`typeof`傳回: 「"數字、"字串，"「 布林 」，「 物件 」 [函式] 和"undefined"。  
  
 括號中是選用的`typeof`語法。  
  
## <a name="example"></a>範例  
 下列範例會測試變數的資料類型。  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>範例  
 下列範例會測試的資料類型為`undefined`宣告與未宣告的變數。  
  
```JavaScript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Array.isArray 函式](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf 函式](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [undefined 的常數](../../javascript/reference/undefined-constant-javascript.md)   
 [比較運算子](../../javascript/reference/comparison-operators-javascript.md)   
 [資料類型](../../javascript/data-types-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)