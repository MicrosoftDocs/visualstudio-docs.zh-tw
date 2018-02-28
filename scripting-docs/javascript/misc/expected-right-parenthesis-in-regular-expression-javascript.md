---
title: "必須是 &#39;) &#39;在規則運算式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4560c638cc0e9209141ba9b0878208eb84eb0c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>必須是 &#39;) &#39;在規則運算式 (JavaScript)
您嘗試建立規則運算式的擷取、 判斷提示或群組，但不是含右括號。 括號中的規則運算式有多種用途。 它們主要是用來擷取子運算式，若要指定判斷提示，或組成模式，項目可以視為單一單位的 *，+，？，依此類推。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   加入在最右邊的右括號。  
  
    > [!NOTE]
    >  如果您想要比對單一括號，逸出反斜線- \\(使它不會解譯為特殊字元- [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)