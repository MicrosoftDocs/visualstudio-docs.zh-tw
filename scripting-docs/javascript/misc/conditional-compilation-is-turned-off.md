---
title: "條件式編譯已經關閉 |Microsoft 文件"
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-is-turned-off"></a>條件式編譯已經關閉
您嘗試上使用條件式編譯變數，而不進行第一次開啟條件式編譯。 開啟 條件式編譯會告知[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]編譯器將解譯開頭為 @ 做為條件式編譯變數的識別項。 您可以從您的陳述式的條件式程式碼：  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將下列陳述式加入至條件式程式碼的開頭：  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on陳述式](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if陳述式](../../javascript/reference/at-if-statement-javascript.md)   
 [@set 陳述式](../../javascript/reference/at-set-statement-javascript.md)