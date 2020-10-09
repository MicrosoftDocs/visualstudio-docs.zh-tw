---
title: 未結束的批註 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8453b05d2d09537f381bd2947dccb6b0a19a6263
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861842"
---
# <a name="unterminated-comment"></a>未結束的註解
您已開始多行批註區塊，但未正確地將它終止。 多行批註的開頭為 "/*" 組合，結尾為反向的 " \* /" 組合。 下列為範例：  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請務必使用 "*/" 來終止多行批註。  
  
## <a name="see-also"></a>請參閱  
 [Comment 陳述式](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)