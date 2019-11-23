---
title: 條件式編譯已關閉 |Microsoft Docs
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
ms.openlocfilehash: 56621d6f7fcc195a4ece7654adeafd1096c37e8b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572936"
---
# <a name="conditional-compilation-is-turned-off"></a>條件式編譯已經關閉
您嘗試使用條件式編譯變數，而不需要先開啟的條件式編譯。 開啟條件式編譯會告訴 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 編譯器以 @ 當做條件式編譯變數來解讀以 @ 開頭的識別碼。 您可以使用語句來開始您的條件式程式碼，來完成此動作：  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>若要改正這項錯誤  
  
- 將下列語句新增至條件式程式碼的開頭：  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on 語句](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if 語句](../../javascript/reference/at-if-statement-javascript.md)   
 [@set 陳述式](../../javascript/reference/at-set-statement-javascript.md)