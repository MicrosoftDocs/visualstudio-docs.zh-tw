---
title: 字元集中的範圍無效 (JavaScript) |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a81634a96fb85584c9176db8c72bfc5c3468dc2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816874"
---
# <a name="invalid-range-in-character-set-javascript"></a>不正確的字元集範圍 (JavaScript)
您嘗試使用不正確字元集範圍來建立正則運算式。 字元集的範圍必須僅限單一字元，例如 a-z 或 0-9;字元類別（例如 \w）不能包含在字元集中。 範圍中的第一個字元也必須位於範圍中的第二個字元之前。 例如：  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請只使用單一字元來撰寫您的正則運算式字元集，並確定它們的順序正確。  
  
## <a name="see-also"></a>另請參閱  
 [正則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [ (JavaScript) 的正則運算式語法 ](https://msdn.microsoft.com/library/1400241x)