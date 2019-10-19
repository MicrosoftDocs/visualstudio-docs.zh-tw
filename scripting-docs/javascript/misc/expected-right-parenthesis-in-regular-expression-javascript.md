---
title: 正則運算式中必須是 '） ' （JavaScript） |Microsoft Docs
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
ms.openlocfilehash: 7c10449df9ef3331949695b7423da3eb08b65433
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577544"
---
# <a name="expected--in-regular-expression-javascript"></a>在規則運算式中必須是 ')' (JavaScript)
您嘗試建立正則運算式 capture、判斷提示或群組，但未包含右括弧。 括弧在正則運算式中有數個用途。 主要是用來捕捉子運算式、指定判斷提示，或將模式群組在一起，以便將專案視為單一單位（依 *、+、？等等）。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 新增最右邊的右括弧。  
  
    > [!NOTE]
    > 如果您想要比對單一括弧，請使用反斜線-\\ （-因此不會 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 將它解讀為特殊字元。  
  
## <a name="see-also"></a>請參閱  
 [正則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [正則運算式語法（JavaScript）](https://msdn.microsoft.com/library/1400241x)