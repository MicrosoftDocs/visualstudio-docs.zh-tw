---
title: JavaScript)  (非預期的數量詞 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: da4ff08ae667b868670364c7ad6b9a6b69ae6ad3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815327"
---
# <a name="unexpected-quantifier-javascript"></a>非預期的數量詞 (JavaScript)
撰寫您的正則運算式搜尋模式時，您建立了具有不合法重複因素的 pattern 元素。 例如，模式  
  
```js
/^+/  
```  
  
 是不合法的，因為輸入) 的元素 ^ (開頭不能有重複因素。 下表列出不能有重複因素的元素。  
  
|項目|描述|  
|-------------|-----------------|  
|^|輸入的開頭|  
|$|輸入結尾|  
|\b|字邊界|  
|\B|非字邊界|  
|*|零個以上的重複|  
|+|一或多個重複|  
|?|零次或一次重複|  
|n-1|n 次重複|  
|{n，}|n 個以上的重複|  
|{n，m}|從 n 到 m 次重複（含）|  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 確定您的搜尋模式元素只包含合法的重複因素。  
  
## <a name="see-also"></a>另請參閱  
 [正則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [ (JavaScript) 的正則運算式語法 ](https://msdn.microsoft.com/library/1400241x)