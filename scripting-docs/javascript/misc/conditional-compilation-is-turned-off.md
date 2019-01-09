---
title: 條件式編譯已經關閉 |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcbf844ced2bb74ddfea9bd62d68877b7a3c969c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092881"
---
# <a name="conditional-compilation-is-turned-off"></a>條件式編譯已經關閉
您嘗試使用不含第一次開啟的條件式編譯的條件式編譯變數上。 開啟 條件式編譯會告訴[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]編譯器解譯開頭為 @ 做為條件式編譯變數的識別項。 您可以從您使用陳述式的條件式程式碼：  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   條件式程式碼的開頭加入下列陳述式：  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on 陳述式](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if 陳述式](../../javascript/reference/at-if-statement-javascript.md)   
 [@set 陳述式](../../javascript/reference/at-set-statement-javascript.md)