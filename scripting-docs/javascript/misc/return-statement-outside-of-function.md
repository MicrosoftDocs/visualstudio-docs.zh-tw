---
description: 您已在程式碼的全域範圍中使用 return 語句。
title: 函式外部的 ' return ' 語句 |Microsoft 檔
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
ms.openlocfilehash: c275db9b2b13f6730ef62a757502b1d51a59ee43
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571658"
---
# <a name="return-statement-outside-of-function"></a>函式外部的 'return' 陳述式
您已 `return` 在程式碼的全域範圍中使用語句。 `return`語句只應出現在函式主體內。  
  
 使用運算子叫用函數 `()` 是運算式。 所有運算式都有值; `return` 語句是用來指定函數所傳回的值。 一般形式為：  
  
```js
  
return [ expression ];  
```  
  
 當 `return` 語句執行時，會評估 *運算式* ，並傳回做為函數的值。 如果沒有運算式，則會傳回 **undefined** 。  
  
 當語句執行時 `return` ，即使函式主體中仍有其他語句，也會停止執行函數。 這項規則的例外狀況是，如果 **return** 語句出現在 **try** 區塊中，而且有對應的 **finally** 區塊，則 **finally** 區塊中的程式碼會在函式傳回之前執行。  
  
 如果函式因為到達函式主體的結尾而未執行 `return` 語句而傳回，則傳回的值會是 **未定義** 的值 (這表示函數結果無法當做較大運算式) 的一部分使用。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- `return`從程式碼的主體 (全域範圍) 移除語句。  
  
## <a name="see-also"></a>另請參閱  
 [return 語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/return)   
 [Function 物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [caller 屬性 (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/caller)
