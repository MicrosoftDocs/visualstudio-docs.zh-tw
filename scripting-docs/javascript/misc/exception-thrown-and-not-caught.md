---
title: "發生例外狀況而且未攔截到 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="exception-thrown-and-not-caught"></a>發生例外狀況而且未攔截
包含您`throw`陳述式中程式碼，但它不住**再試一次**區塊，不足或沒有相關聯**攔截**區塊來攔截錯誤。 從擲回例外狀況**再試一次**封鎖使用**擲回**陳述式，並已攔截外**再試一次**區塊**攔截**陳述式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   括住中擲回例外狀況的程式碼**再試一次**區塊，並確定沒有相對應**攔截**區塊。  
  
-   請確定您的 catch 陳述式所預期的例外狀況的正確格式。  
  
-   如果重新擲回例外狀況，請確定另一個對應的 catch 陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [Error 物件](../../javascript/reference/error-object-javascript.md)   
 [throw 陳述式](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)