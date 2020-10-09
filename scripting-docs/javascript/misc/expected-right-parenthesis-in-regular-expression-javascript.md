---
title: 正則運算式中必須是 ' ) ' (JavaScript) |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 29b25b5ab48ffe0a9a9dfafa9e60d66913c5e25e
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861893"
---
# <a name="expected--in-regular-expression-javascript"></a>在規則運算式中必須是 ')' (JavaScript)
您嘗試建立正則運算式捕捉、判斷提示或群組，但未包含右括弧。 括弧在正則運算式中有數個用途。 主要是用來捕捉子運算式、指定判斷提示，或是將模式群組在一起，讓專案可以依 *、+、？等等視為單一單位。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 新增最右邊的右括弧。  
  
    > [!NOTE]
    > 如果您想要比對單一括弧，請使用反斜線 ( 將其取消， \\ 如此就不會將它解讀為特殊字元 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 。  
  
## <a name="see-also"></a>請參閱  
 [正則運算式物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [ (JavaScript) 的正則運算式語法 ](/previous-versions/1400241x(v=vs.100))