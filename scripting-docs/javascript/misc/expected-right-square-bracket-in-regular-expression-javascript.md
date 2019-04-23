---
title: 必須是 ']' 中規則運算式 (JavaScript) |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 5c49ab90dae8f30dae075906bb9c7ecb7881428f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065073"
---
# <a name="expected--in-regular-expression-javascript"></a>在規則運算式中必須是 ']' (JavaScript)
您嘗試建立的規則運算式比對的字元類別，但並未包含右方括號。 個別的常值字元的組合可以組成的字元類別，藉由將它們放在方括號內。 字元類別符合其中任何一個字元。 例如，/ [abc] / 符合任何一個字母"a"、"b"或"c"。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 規則運算式中加上右括弧。  
  
    > [!NOTE]
    >  如果您想要比對單一括號，再加上反斜線- \\[-因此它將不會解譯為特殊字元[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](https://msdn.microsoft.com/library/1400241x)