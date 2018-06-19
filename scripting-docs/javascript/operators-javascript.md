---
title: 運算子 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, operators
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3068a609da2468c59066ccd38f6de87cef1ed17
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
ms.locfileid: "29753267"
---
# <a name="operators-javascript"></a>運算子 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 具有完整範圍的運算子，包含算術、邏輯、位元、指派，以及一些雜項運算子。 如需說明和範例，請參閱特定運算子的主題。  
  
## <a name="computational-operators"></a>計算運算子  
  
|描述|符號|  
|-----------------|------------|  
|[一元否定運算](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
|[遞增](../javascript/reference/increment-and-decrement-operators-javascript.md)|++|  
|[遞減](../javascript/reference/increment-and-decrement-operators-javascript.md)|--|  
|[乘法](../javascript/reference/multiplication-operator-decrement-javascript.md)|*|  
|[除法](../javascript/reference/division-operator-decrement-javascript.md)|/|  
|[算術餘數](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[加法](../javascript/reference/addition-operator-decrement-javascript.md)|+|  
|[減法](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
  
## <a name="logical-operators"></a>邏輯運算子  
  
|描述|符號|  
|-----------------|------------|  
|[邏輯 NOT](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|!|  
|[小於](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[大於](../javascript/reference/comparison-operators-javascript.md)|>|  
|[小於或等於](../javascript/reference/comparison-operators-javascript.md)|\<=|  
|[大於或等於](../javascript/reference/comparison-operators-javascript.md)|>=|  
|[相等](../javascript/reference/comparison-operators-javascript.md)|==|  
|[不等](../javascript/reference/comparison-operators-javascript.md)|!=|  
|[邏輯 AND](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[邏輯 OR](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[條件 (三元)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[逗號](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[嚴格相等](../javascript/reference/comparison-operators-javascript.md)|===|  
|[嚴格不等](../javascript/reference/comparison-operators-javascript.md)|!==|  
  
## <a name="bitwise-operators"></a>位元運算子  
  
|描述|符號|  
|-----------------|------------|  
|[位元 NOT](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[位元左移](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|<\<|  
|[位元右移](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|>>|  
|[不帶正負號的右移](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|>>>|  
|[位元 AND](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[位元 XOR](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[位元 OR](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## <a name="assignment-operators"></a>指派運算子  
  
|描述|符號|  
|-----------------|------------|  
|[指派](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|=|  
|[複合指派](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*= (例如 += 和 &=)|  
  
## <a name="miscellaneous-operators"></a>雜項運算子  
  
|描述|符號|  
|-----------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|刪除|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|中的|  
  
## <a name="equality-and-strict-equality"></a>相等和嚴格相等  
 == (相等) 與 === (嚴格相等) 之間的差異在於相等運算子會先強制不同類型的值，再檢查是否相等。 例如，比較字串"1" 與數字 1 時會比較為 true。 相反地，嚴格相等運算子不會將值強制為不同類型，因此字串 "1" 與數字 1 比較起來不相等。  
  
 基本字串、數字和布林值是依值進行比較。 如果它們的值相同，則相等。 物件 (包含 `Array`、`Function`、`String`、**Number**、`Boolean`、**Error**、`Date` 和 `RegExp` 物件) 是以傳址方式比較。 即使這些類型的兩個變數擁有相同的值，它們也只有在指向完全相同的物件時才會相等。  
  
 例如:   
  
```JavaScript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```