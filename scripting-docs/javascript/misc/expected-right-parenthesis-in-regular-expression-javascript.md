---
title: 必須是 ')' 在規則運算式 (JavaScript) |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72b4cf24b4b738b7ca71e364d7be6486313a4844
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840801"
---
# <a name="expected--in-regular-expression-javascript"></a>在規則運算式中必須是 ')' (JavaScript)
您嘗試建立規則運算式的擷取、 判斷提示或群組，但並未包含的右括號。 括號內會有多種用途，規則運算式中。 它們主要是用來擷取子運算式，指定判斷提示，或將群組模式在一起，讓項目可以視為單一單位的 *，+，？，依此類推。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   新增最右邊的左括號。  
  
    > [!NOTE]
    >  如果您想要比對單一括號，再加上反斜線- \\(使它將不會解譯為特殊字元- [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](https://msdn.microsoft.com/library/1400241x)