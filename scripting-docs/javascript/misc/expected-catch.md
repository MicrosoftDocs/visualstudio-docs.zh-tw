---
title: 必須是 'catch' |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 244635605abafc5c0bd22c5203b105aa6e7dc669
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2018
ms.locfileid: "53801972"
---
# <a name="expected-catch"></a>必須是 'catch'
使用例外狀況處理**嘗試**封鎖，但不是撰寫相關聯**攔截**陳述式。 例外狀況處理機制需要的程式碼，可能會失敗，發生例外狀況時，不應執行的程式碼會包裝在內**嘗試**區塊。 內擲回例外狀況**嘗試**封鎖使用**擲回**陳述式，並已攔截外部**嘗試**具有一或多個區塊**攔截**陳述式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   加入相關聯**攔截**區塊。  
  
-   請嘗試使用**最後**而不是封鎖**攔截**區塊。  
  
## <a name="see-also"></a>另請參閱  
 [try...try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error 物件](../../javascript/reference/error-object-javascript.md)