---
title: 字元集中的範圍無效（JavaScript） |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 29f28f0ceeb6bd1bf0a8f28438afd803d3a9a9ac
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576626"
---
# <a name="invalid-range-in-character-set-javascript"></a>不正確的字元集範圍 (JavaScript)
您嘗試使用不正確字元集範圍來建立正則運算式。 字元集的範圍必須僅限單一字元，例如 a-z 或 0-9;您不能在字元集中包含字元類別（例如 \w）。 範圍中的第一個字元也必須位於範圍中的第二個字元之前。 例如:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請只使用單一字元來撰寫正則運算式字元集，並確定它們是以正確的順序排列。  
  
## <a name="see-also"></a>請參閱  
 [正則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [正則運算式語法（JavaScript）](https://msdn.microsoft.com/library/1400241x)