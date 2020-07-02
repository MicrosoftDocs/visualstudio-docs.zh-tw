---
title: 正則運算式中必須是 '] ' （JavaScript） |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a2a2b83b818e37c0b62e103fe284c5c4d110c6c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815626"
---
# <a name="expected--in-regular-expression-javascript"></a>在規則運算式中必須是 ']' (JavaScript)
您嘗試建立正則運算式比對的字元類別，但未包含右括弧。 個別的常值字元組合可以組合成字元類別，方法是將它們放在方括弧內。 字元類別符合其中包含的任何一個字元。 例如，/[abc]/符合任何一個字母 "a"、"b" 或 "c"。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 在正則運算式中加入右括弧。  
  
    > [!NOTE]
    > 如果您想要比對單一方括弧，請使用反斜線- \\ [-，使其不會被視為特殊字元 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 。  
  
## <a name="see-also"></a>另請參閱  
 [正則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [正則運算式語法（JavaScript）](https://msdn.microsoft.com/library/1400241x)