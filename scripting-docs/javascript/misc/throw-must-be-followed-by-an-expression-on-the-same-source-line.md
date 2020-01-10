---
title: Throw 後面必須接在相同原始程式列的運算式 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572757"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>throw 必須接著一運算式，且於同一行程式碼
您使用了 `throw` 關鍵字，但未在相同原始程式列上使用運算式來追蹤它。 `throw` 語句包含兩個部分： `throw` 關鍵字，後面接著要擲回的運算式。 例如：  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 您無法將這兩個元件分割。  
  
### <a name="to-correct-this-error"></a>若要改正這項錯誤  
  
- 請確定要擲回的 `throw` 關鍵字和運算式出現在同一行上。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤物件](../../javascript/reference/error-object-javascript.md)   
 [Throw 語句](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)