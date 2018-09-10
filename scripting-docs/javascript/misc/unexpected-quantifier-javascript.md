---
title: 未預期的數量詞 (JavaScript) |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef0955bac35009d9b6c82f1856bb9005a08043ad
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282258"
---
# <a name="unexpected-quantifier-javascript"></a>非預期的數量詞 (JavaScript)
當您在撰寫您的規則運算式搜尋模式，您會建立含不合法的重複子模式項目。 例如，模式  
  
```  
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
|{n}|n 個或多個重複項目|  
|{n，m}|從 n 到 m 重複項目，內含|  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定您的搜尋模式項目包含只有合法重複因素。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](https://msdn.microsoft.com/library/1400241x)