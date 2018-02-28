---
title: "有未結束的註解 |Microsoft 文件"
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
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fde5d5edd7e81060b088e4940d752aa05e65ded
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="unterminated-comment"></a>未結束的註解
您已經開始多行註解區塊中，但未正確地終止它。 開頭為多行註解"/ * 」 組合，並以相反順序的結尾 」\*/ 」 組合。 以下是一個範例：  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確定要終止多行註解"* /"。  
  
## <a name="see-also"></a>另請參閱  
 [Comment 陳述式](../../javascript/reference/comment-statements-javascript.md)