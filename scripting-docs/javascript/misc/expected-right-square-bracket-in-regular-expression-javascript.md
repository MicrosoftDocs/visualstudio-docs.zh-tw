---
title: "必須是 &#39;]&#39;在規則運算式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c59dcbeea91a1bc01e870d0a49fd22cace6562d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>必須是 &#39;]&#39;在規則運算式 (JavaScript)
您嘗試建立的規則運算式比對的字元類別，但未包含右方括號。 可以將它們放入方括號內，將個別的常值字元組合組合成字元類別。 字元類別符合其中任何一個字元。 例如，/ [abc] / 符合任何一個字母"a"、"b"或"c"。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   加入的規則運算式的右括號。  
  
    > [!NOTE]
    >  如果您想要比對單一括號，逸出反斜線- \\[，讓它將不會解譯為特殊字元的[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)