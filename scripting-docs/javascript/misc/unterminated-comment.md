---
title: 未結束的註解 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2b21c585bb48b55929a78554d686477e0fa5649
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842438"
---
# <a name="unterminated-comment"></a>未結束的註解
您開始為多行註解區塊，但並未正確地終止它。 開頭為多行註解"/ * 」 組合，並以反向結尾 」\*/ 」 組合。 以下是一個範例：  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確定要終止多行註解 」 * /"。  
  
## <a name="see-also"></a>另請參閱  
 [Comment 陳述式](../../javascript/reference/comment-statements-javascript.md)