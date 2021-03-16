---
description: 您已使用 throw 關鍵字，但未在相同的原始程式列上使用運算式。
title: Throw 後面必須接著相同原始程式列上的運算式 |Microsoft 檔
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: cfa2bace6f82ae972204cc0a405cc7e8682e98af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570709"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>throw 必須接著一運算式，且於同一行程式碼
您已使用 `throw` 關鍵字，但未在相同的原始程式列上使用運算式。 `throw`語句是由兩個部分所組成： `throw` 關鍵字，後面接著要擲回的運算式。 例如：  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 您無法將這兩個元件分割。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定要擲回的 `throw` 關鍵字和運算式出現在同一行上。  
  
## <a name="see-also"></a>另請參閱  
 [Error 物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw 語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [嘗試。。。抓住。。。finally 語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)
