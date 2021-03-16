---
description: 您已使用例外狀況處理 try 區塊，但未寫入相關聯的 catch 語句。
title: 應為 ' catch ' |Microsoft 檔
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5cf6087ff5a299c575ac4f2cd5eb8a3e206b7e0
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571034"
---
# <a name="expected-catch"></a>必須是 'catch'
您已使用例外狀況處理 **try** 區塊，但未寫入相關聯的 **catch** 語句。 例外狀況處理機制要求可能失敗的程式碼，以及例外狀況發生時不應執行的程式碼會包裝在 **try** 區塊內。 使用 throw 語句從 **try** 區塊內 **擲** 回例外狀況，並使用一或多個 **catch** 語句攔截到 **try** 區塊之外。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 加入關聯的 **catch** 區塊。  
  
- 請嘗試使用 **finally** 區塊，而不是 **catch** 區塊。  
  
## <a name="see-also"></a>另請參閱  
 [嘗試。。。抓住。。。finally 語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Error 物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)
