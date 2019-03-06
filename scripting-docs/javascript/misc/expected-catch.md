---
title: 必須是 'catch' |Microsoft Docs
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
ms.openlocfilehash: 4a25f72fccfd072243d6d0fdfd1d311c1a3bb6f4
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841442"
---
# <a name="expected-catch"></a>必須是 'catch'
使用例外狀況處理**嘗試**封鎖，但不是撰寫相關聯**攔截**陳述式。 例外狀況處理機制需要的程式碼，可能會失敗，發生例外狀況時，不應執行的程式碼會包裝在內**嘗試**區塊。 內擲回例外狀況**嘗試**封鎖使用**擲回**陳述式，並已攔截外部**嘗試**具有一或多個區塊**攔截**陳述式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   加入相關聯**攔截**區塊。  
  
-   請嘗試使用**最後**而不是封鎖**攔截**區塊。  
  
## <a name="see-also"></a>另請參閱  
 [try...try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error 物件](../../javascript/reference/error-object-javascript.md)