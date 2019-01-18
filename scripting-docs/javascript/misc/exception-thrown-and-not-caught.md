---
title: 發生例外狀況，而且未攔截到 |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349032"
---
# <a name="exception-thrown-and-not-caught"></a>發生例外狀況而且未攔截
您包含`throw`陳述式中您的程式碼，但不住**試**區塊中，或不相關聯**攔截**區塊來捕捉此錯誤。 內擲回例外狀況**嘗試**封鎖使用**擲回**陳述式，並已攔截外部**試**區塊**攔截**陳述式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   括住中擲回例外狀況的程式碼**嘗試**區塊中，並確保沒有相對應**攔截**區塊。  
  
-   請確定您的 catch 陳述式預期的例外狀況的正確格式。  
  
-   如果重新擲回例外狀況，請確定另一個對應的 catch 陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [Error 物件](../../javascript/reference/error-object-javascript.md)   
 [Throw 陳述式](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)