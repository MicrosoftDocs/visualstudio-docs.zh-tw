---
title: "&#39; 傳回 &#39;外部函式的陳述式 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="39return39-statement-outside-of-function"></a>&#39; 傳回 &#39;外部函式的陳述式
您使用`return`在全域範圍內的陳述式，您的程式碼。 `return`陳述式應該只出現在函式主體內。  
  
 叫用的函式`()`運算子是一個運算式。 所有運算式都有的值;`return`陳述式用來指定函數所傳回的值。 一般格式如下：  
  
```  
  
return [ expression ];  
```  
  
 當`return`執行陳述式，*運算式*會評估並傳回做為函式的值。 如果沒有運算式，**未定義**傳回。  
  
 此函式的執行會停止時`return`執行陳述式，即使有其他陳述式的函式主體中。 此規則的例外狀況是如果**傳回**陳述式內，就會發生**再試一次**區塊，而且沒有相對應**最後**封鎖，程式碼**最後**函式傳回前，區塊會執行。  
  
 如果函式傳回，因為它達到函式主體的結尾，而不執行`return`陳述式，傳回的值是**未定義**值 （這表示函式的結果不能做為較大運算式的一部分).  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除`return`陳述式，從您的程式碼 （全域範圍） 的主體。  
  
## <a name="see-also"></a>另請參閱  
 [return 陳述式](../../javascript/reference/return-statement-javascript.md)   
 [函式物件](../../javascript/reference/function-object-javascript.md)   
 [caller 屬性 (Function)](../../javascript/reference/caller-property-function-javascript.md)