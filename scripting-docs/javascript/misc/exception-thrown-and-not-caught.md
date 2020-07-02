---
title: 擲回例外狀況，但未攔截 |Microsoft Docs
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
ms.openlocfilehash: 44f207d2e32a7ca79ee0d5851a80261c5da9743d
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814586"
---
# <a name="exception-thrown-and-not-caught"></a>發生例外狀況而且未攔截
您 `throw` 在程式碼中包含了語句，但它並未包含在**try**區塊內，或沒有相關聯的**catch**區塊可攔截錯誤。 例外狀況是從**try**區塊內使用 throw 語句**來擲**回，並使用**catch**語句攔截到**try**區塊外。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將可在**try**區塊中擲回例外狀況的程式碼括住，並確保有對應的**catch**區塊。  
  
- 請確定您的 catch 語句預期會有正確的例外狀況格式。  
  
- 如果重新擲回例外狀況，請確定有另一個對應的 catch 語句。  
  
## <a name="see-also"></a>另請參閱  
 [Error 物件](../../javascript/reference/error-object-javascript.md)   
 [throw 語句](../../javascript/reference/throw-statement-javascript.md)   
 [嘗試 .。。catch .。。finally 語句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)