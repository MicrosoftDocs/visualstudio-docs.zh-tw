---
title: "Throw 必須接著運算式，且於同一行程式碼 |Microsoft 文件"
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
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7179a22d2713c9ddc894618bd6921f3f873f2ad8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>throw 必須接著一運算式，且於同一行程式碼
您使用`throw`關鍵字，但未遵循它與運算式相同的原始程式行上。 A`throw`陳述式包含兩個部分：`throw`關鍵字，後面接著擲回運算式。 例如：  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 您無法分割這兩個元件。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定`throw`關鍵字，並擲回運算式出現在同一行。  
  
## <a name="see-also"></a>另請參閱  
 [Error 物件](../../javascript/reference/error-object-javascript.md)   
 [throw 陳述式](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)