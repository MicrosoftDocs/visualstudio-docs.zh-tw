---
title: typeof 運算子 (JavaScript) |Microsoft 文件
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
- typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9ff8c7942c773d138dd599956c41d1e583e6288
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
ms.locfileid: "29899626"
---
# <a name="typeof-operator-javascript"></a>typeof 運算子 (JavaScript)
傳回可識別運算式之資料類型的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>備註  
 *運算式*引數是任何類型資訊所要搜尋的運算式。  
  
 `typeof`運算子會傳回做為字串的類型資訊。 有七個可能值的`typeof`傳回: 「"數字、"字串，""，則為 true，""物件、"[函式，]"未定義 」 和 「 未知 」。  
  
 括號中是選用的`typeof`語法。  

 物件可能會傳回為 XMLHTTPRequest 中未知的類型。 在 JavaScript 中的任何類比與 COM 物件也可能會傳回與未知的類型。
  
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
  
## <a name="see-also"></a>請參閱  
 [Array.isArray 函式](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf Function](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [undefined 的常數](../../javascript/reference/undefined-constant-javascript.md)   
 [比較運算子](../../javascript/reference/comparison-operators-javascript.md)   
 [資料類型](../../javascript/data-types-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)