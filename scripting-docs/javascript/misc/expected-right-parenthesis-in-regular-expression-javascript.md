---
title: 必須是&#39;)&#39;中的規則運算式 (JavaScript) |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d1075a41d2b97d10166b1372e8df3a93dd9d8e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279124"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>必須是&#39;)&#39;中的規則運算式 (JavaScript)
您嘗試建立規則運算式的擷取、 判斷提示或群組，但並未包含的右括號。 括號內會有多種用途，規則運算式中。 它們主要是用來擷取子運算式，指定判斷提示，或將群組模式在一起，讓項目可以視為單一單位的 *，+，？，依此類推。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   新增最右邊的左括號。  
  
    > [!NOTE]
    >  如果您想要比對單一括號，再加上反斜線- \\(使它將不會解譯為特殊字元- [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](https://msdn.microsoft.com/library/1400241x)