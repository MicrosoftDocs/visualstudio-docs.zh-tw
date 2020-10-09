---
title: 擲回但未攔截的例外狀況 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862759"
---
# <a name="exception-thrown-and-not-caught"></a>發生例外狀況而且未攔截
您 `throw` 已在程式碼中包含語句，但未在 **try** 區塊內，或沒有相關聯的 **catch** 區塊來攔截錯誤。 使用 throw 語句從**try**區塊內**擲**回例外狀況，並使用**catch**語句在**try**區塊外部捕捉例外狀況。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 在 **try** 區塊中括住可能擲回例外狀況的程式碼，並確定有對應的 **catch** 區塊。  
  
- 請確定您的 catch 語句預期會有正確形式的例外狀況。  
  
- 如果重新擲回例外狀況，請確定有另一個對應的 catch 語句。  
  
## <a name="see-also"></a>請參閱  
 [Error 物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw 語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [嘗試。。。抓住。。。finally 語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)