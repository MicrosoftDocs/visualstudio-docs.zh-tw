---
title: 函式外部的 ' return ' 語句 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32eadcf5ae88dbe64c8ccdb3effbb85bc79f9b32
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816731"
---
# <a name="return-statement-outside-of-function"></a>函式外部的 'return' 陳述式
您在 `return` 程式碼的全域範圍中使用了語句。 `return`語句應該只會出現在函式的主體中。  
  
 使用運算子叫用函數 `()` 是運算式。 所有運算式都有值;`return`語句可用來指定函式所傳回的值。 一般的形式如下：  
  
```js
  
return [ expression ];  
```  
  
 `return`執行語句時，會評估*expression*並傳回做為函數的值。 如果沒有運算式，則會傳回**undefined** 。  
  
 執行語句時，函式會停止執行 `return` ，即使函式主體中仍有其他語句存在也一樣。 此規則的例外狀況是，如果**return**語句出現在**try**區塊內，而且有對應的**finally**區塊，則**finally**區塊中的程式碼會在函式傳回之前執行。  
  
 如果函式因為到達函式主體的結尾而未執行 `return` 語句而傳回，則傳回的值會是**未定義**的值（這表示函數結果不能當做較大運算式的一部分使用）。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- `return`從程式碼的主要主體（全域範圍）移除語句。  
  
## <a name="see-also"></a>另請參閱  
 [return 語句](../../javascript/reference/return-statement-javascript.md)   
 [Function 物件](../../javascript/reference/function-object-javascript.md)   
 [caller 屬性 (Function)](../../javascript/reference/caller-property-function-javascript.md)