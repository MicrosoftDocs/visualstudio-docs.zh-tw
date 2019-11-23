---
title: 擲回例外狀況，但未攔截 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572863"
---
# <a name="exception-thrown-and-not-caught"></a>發生例外狀況而且未攔截
您在程式碼中包含了 `throw` 語句，但未括住在**try**區塊內，或沒有相關聯的**catch**區塊可攔截錯誤。 例外狀況是從**try**區塊內使用 throw 語句**來擲**回，並使用**catch**語句攔截到**try**區塊外。  
  
### <a name="to-correct-this-error"></a>若要改正這項錯誤  
  
- 將可在**try**區塊中擲回例外狀況的程式碼括住，並確保有對應的**catch**區塊。  
  
- 請確定您的 catch 語句預期會有正確的例外狀況格式。  
  
- 如果重新擲回例外狀況，請確定有另一個對應的 catch 語句。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤物件](../../javascript/reference/error-object-javascript.md)   
 [Throw 語句](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)