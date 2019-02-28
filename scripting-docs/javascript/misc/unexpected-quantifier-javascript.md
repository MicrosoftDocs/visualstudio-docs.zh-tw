---
title: 未預期的數量詞 (JavaScript) |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f18195f344adca16fce7403d225c42826a2af544
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843399"
---
# <a name="unexpected-quantifier-javascript"></a>非預期的數量詞 (JavaScript)
當您在撰寫您的規則運算式搜尋模式，您會建立含不合法的重複子模式項目。 例如，模式  
  
```js
/^+/  
```  
  
 不合法因為項目 ^ （輸入開頭） 不能有重複的因素。 下表列出的項目不能有重複的因素。  
  
|元素|描述|  
|-------------|-----------------|  
|^|輸入開頭|  
|$|Konec vstupu|  
|\b|字邊界|  
|\B|非字邊界|  
|*|零或多個重複項目|  
|+|一或多個重複項目|  
|?|零個或一個重複項目|  
|{n}|n 個重複項目|  
|{n,}|n 個或多個重複項目|  
|{n,m}|從 n 到 m 重複項目，內含|  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定您的搜尋模式項目包含只有合法重複因素。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](https://msdn.microsoft.com/library/1400241x)