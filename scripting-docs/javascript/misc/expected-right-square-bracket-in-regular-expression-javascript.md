---
title: 必須是&#39;]&#39;中的規則運算式 (JavaScript) |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64ef929ba309f0b496e72f3cf740daf6970d08fb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283713"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>必須是&#39;]&#39;中的規則運算式 (JavaScript)
您嘗試建立的規則運算式比對的字元類別，但並未包含右方括號。 個別的常值字元的組合可以組成的字元類別，藉由將它們放在方括號內。 字元類別符合其中任何一個字元。 例如，/ [abc] / 符合任何一個字母"a"、"b"或"c"。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   規則運算式中加上右括弧。  
  
    > [!NOTE]
    >  如果您想要比對單一括號，再加上反斜線- \\[-因此它將不會解譯為特殊字元[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](https://msdn.microsoft.com/library/1400241x)