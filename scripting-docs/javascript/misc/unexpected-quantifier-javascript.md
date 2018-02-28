---
title: "未預期的數量詞 (JavaScript) |Microsoft 文件"
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb6d6d3129057c399dd7369c6f69eb7396f07ab4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="unexpected-quantifier-javascript"></a>非預期的數量詞 (JavaScript)
當您在撰寫規則運算式搜尋模式，您會建立包含不合法的重複因數模式項目。 例如，模式  
  
```  
/^+/  
```  
  
 不合法因為項目 ^ （輸入開頭） 不能有重複的因素。 下表列出的項目不能有重複的因素。  
  
|項目|說明|  
|-------------|-----------------|  
|^|輸入開頭|  
|$|以輸入結尾|  
|\b|字邊界|  
|\B|非字邊界|  
|*|零或多個重複項目|  
|+|一或多個重複項目|  
|?|零個或一個重複項目|  
|{n}|重複 n 次|  
|{n}|n 個或多個重複項目|  
|{n，m}|N，m 重複，內含從|  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確認您的搜尋模式項目包含只有合法的重複因素。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)