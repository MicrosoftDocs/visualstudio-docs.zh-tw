---
title: 必須是 ' catch ' |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8cad981e4ba469f67645aca601e6b58c18e1fab6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573436"
---
# <a name="expected-catch"></a>必須是 'catch'
您使用了例外狀況處理**try**區塊，但是並未寫入相關聯的**catch**語句。 例外狀況處理機制會要求可能失敗的程式碼，以及例外狀況發生時不應執行的程式碼，包裝在**try**區塊內。 例外狀況是從**try**區塊內使用 throw 語句**來擲**回，並使用一或多個**catch**語句攔截在**try**區塊外。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 新增相關聯的**catch**區塊。  
  
- 嘗試使用**finally**區塊，而不是**catch**區塊。  
  
## <a name="see-also"></a>請參閱  
 [嘗試 .。。catch .。。finally 語句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error 物件](../../javascript/reference/error-object-javascript.md)