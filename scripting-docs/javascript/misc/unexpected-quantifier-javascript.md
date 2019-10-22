---
title: 非預期的數量詞（JavaScript） |Microsoft Docs
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
ms.openlocfilehash: 2070ec6ad01eb62c6be9b6b9acfc91cba7bc863d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572532"
---
# <a name="unexpected-quantifier-javascript"></a>非預期的數量詞 (JavaScript)
撰寫正則運算式搜尋模式時，您所建立的模式元素具有不合法的重複因素。 例如，模式  
  
```js
/^+/  
```  
  
 不合法，因為元素 ^ （輸入的開頭）不能有重複因素。 下表列出不能有重複因素的元素。  
  
|項目|描述|  
|-------------|-----------------|  
|^|輸入的開頭|  
|$|輸入結尾|  
|\b|字邊界|  
|\B|非字邊界|  
|*|零或多個重複|  
|+|一或多個重複|  
|?|零或一次重複|  
|位|n 重複|  
|{n，}|n 個以上的重複|  
|{n，m}|從 n 到 m 重複（含）|  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定您的搜尋模式元素只包含合法的重複因素。  
  
## <a name="see-also"></a>請參閱  
 [正則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [正則運算式語法（JavaScript）](https://msdn.microsoft.com/library/1400241x)