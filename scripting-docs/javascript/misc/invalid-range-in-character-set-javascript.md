---
title: 不正確的字元範圍設定 (JavaScript) |Microsoft Docs
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
ms.openlocfilehash: 6b1e404a9df368f639530d533b8cf4bf063f8ad6
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842425"
---
# <a name="invalid-range-in-character-set-javascript"></a>不正確的字元集範圍 (JavaScript)
您嘗試使用無效的字元設定的範圍建立規則運算式。 字元集的範圍必須從單一字元，例如 a-z 或 0-9;您不能包含字元類別，例如 \w 中的字元。 也必須在範圍中的第一個字元前面的範圍中，第二個字元。 例如:   
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   若要撰寫您的規則運算式的字元集，並確定在正確的順序也就是使用只能有單一字元。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](https://msdn.microsoft.com/library/1400241x)