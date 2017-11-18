---
title: "Spread 運算子 （...）(JavaScript) |Microsoft 文件"
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
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a07d480360441906c445faa196f6d7771f97d75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="spread-operator--javascript"></a>展開運算子 (...) (JavaScript)
允許從可反覆執行的運算式 (例如其他陣列常值) 初始化陣列常值的某些部分，或允許將運算式展開成多個引數 (在函式呼叫中)。  
  
## <a name="syntax"></a>語法  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## <a name="parameters"></a>參數  
 `iterable`  
 必要項。 可反覆執行的物件。  
  
 `arg0ToN`  
 選擇項。 陣列常值的一個或多個項目。  
  
 `args`  
 選擇項。 函式的一個或多個引數。  
  
## <a name="remarks"></a>備註  
 如需有關迭代器的詳細資訊，請參閱[迭代器和產生器](../../javascript/advanced/iterators-and-generators-javascript.md)。 如需使用展開運算子做為剩餘參數的詳細資訊，請參閱[函式](../../javascript/functions-javascript.md)。  
  
## <a name="example"></a>範例  
 在下列程式碼範例中，會比較使用展開運算子和使用 `concat` 方法的不同。  
  
```JavaScript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何在函式呼叫中使用展開運算子。 在這個範例中，會使用展開運算子將兩個陣列常值傳遞給函式，然後將陣列展開成多個引數。  
  
```JavaScript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## <a name="example"></a>範例  
 透過展開運算子，您可以簡化之前必須使用 `apply` 的程式碼。  
  
```JavaScript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
f.apply(this, args);  
// New method  
f(...args);  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)