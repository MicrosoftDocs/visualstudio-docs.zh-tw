---
title: "'return' 陳述式，函式外的 |Microsoft Docs"
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7c4b71938d960d3825030c42e965b6510ca575b
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802520"
---
# <a name="return-statement-outside-of-function"></a>函式外部的 'return' 陳述式
您已使用`return`全域範圍中的陳述式，您的程式碼。 `return`陳述式應該只出現在函式主體。  
  
 叫用的函式`()`運算子是一個運算式。 所有運算式都有的值;`return`陳述式用來指定函式所傳回的值。 一般格式如下：  
  
```  
  
return [ expression ];  
```  
  
 當`return`陳述式*運算式*評估並傳回做為函式的值。 如果沒有任何運算式中，**未定義**會傳回。  
  
 函式執行時停止`return`執行陳述式，即使有其他陳述式的函式主體中。 此規則的例外狀況是如果**會傳回**陳述式內，就會發生**嘗試**區塊中，且有對應**最後**封鎖，請將程式碼**最後**區塊會執行函式傳回之前。  
  
 如果函式會傳回，因為它達到但不會執行的函式主體的結尾`return`陳述式，傳回的值是**未定義**值 （這表示函式的結果不能做為較大運算式的一部分).  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除`return`陳述式，從您的程式碼 （全域範圍） 的主體。  
  
## <a name="see-also"></a>另請參閱  
 [return 陳述式](../../javascript/reference/return-statement-javascript.md)   
 [函式物件](../../javascript/reference/function-object-javascript.md)   
 [caller 屬性 (Function)](../../javascript/reference/caller-property-function-javascript.md)