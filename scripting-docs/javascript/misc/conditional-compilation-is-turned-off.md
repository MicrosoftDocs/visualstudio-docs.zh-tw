---
title: 條件式編譯已經關閉 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d3c225df20113308ee7037742ad74efb6a0cc2e
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840350"
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