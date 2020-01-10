---
title: 函式外部的 ' return ' 語句 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: a90af6de8e2c238e3660111b19d13c1eaf628c9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573692"
---
# <a name="return-statement-outside-of-function"></a>函式外部的 'return' 陳述式
您在程式碼的全域範圍中使用了 `return` 語句。 `return` 語句應該只會出現在函式的主體內。  
  
 使用 `()` 運算子叫用函數是運算式。 所有運算式都有值;`return` 語句用來指定函數所傳回的值。 一般的形式如下：  
  
```js
  
return [ expression ];  
```  
  
 執行 `return` 語句時，會評估*expression*並傳回做為函數的值。 如果沒有運算式，則會傳回**undefined** 。  
  
 執行 `return` 語句時，會停止執行函式，即使函式主體中仍有其他語句存在也一樣。 此規則的例外狀況是，如果**return**語句出現在**try**區塊內，而且有對應的**finally**區塊，則**finally**區塊中的程式碼會在函式傳回之前執行。  
  
 如果函式傳回，因為它到達函式主體的結尾，而未執行 `return` 語句，則傳回的值會是**未定義**的值（這表示函數結果不能當做較大運算式的一部分使用）。  
  
### <a name="to-correct-this-error"></a>若要改正這項錯誤  
  
- 從程式碼的主要主體（全域範圍）移除 `return` 語句。  
  
## <a name="see-also"></a>另請參閱  
 [return 陳述式](../../javascript/reference/return-statement-javascript.md)   
 [函數物件](../../javascript/reference/function-object-javascript.md)   
 [caller 屬性 (Function)](../../javascript/reference/caller-property-function-javascript.md)