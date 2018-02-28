---
title: "必須是 &#39; catch &#39; |Microsoft 文件"
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="expected-39catch39"></a>必須是 &#39; catch &#39;
使用例外狀況處理**再試一次**會封鎖，但不是撰寫相關聯**攔截**陳述式。 例外狀況處理機制需要的程式碼，可能會失敗，以及發生例外狀況時，不應執行的程式碼會包裝在之內**再試一次**區塊。 從擲回例外狀況**再試一次**封鎖使用**擲回**陳述式，並已攔截外**再試一次**含有一或多個區塊**攔截**陳述式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   新增相關聯**攔截**區塊。  
  
-   請嘗試使用**最後**而不是封鎖**攔截**區塊。  
  
## <a name="see-also"></a>另請參閱  
 [try … try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error 物件](../../javascript/reference/error-object-javascript.md)