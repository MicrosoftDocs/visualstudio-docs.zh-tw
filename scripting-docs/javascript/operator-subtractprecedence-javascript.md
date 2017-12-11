---
title: "運算子優先順序 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- operator precedence
- order of precedence
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82503a312a4a4996e3bd38f596eef3104af3f11b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="operator-precedence-javascript"></a>運算子優先順序 (JavaScript)
運算子優先順序會描述評估運算式時，運算的執行順序。 擁有較高優先順序的作業會在擁有較低優先順序的作業之前執行。 例如，乘法會在加法之前執行。  
  
## <a name="includejavascriptjavascriptincludesjavascript-mdmd-operators"></a>[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 運算子  
 下表列出 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 運算子 (從最高優先順序排到最低優先順序)。 具有相同優先順序的運算子會由左至右評估。  
  
|運算子|描述|  
|--------------|-----------------|  
|. [ ] ( )|欄位存取、陣列索引、函式呼叫和運算式群組|  
|++ -- - ~ ! delete new typeof void|一元運算子、傳回資料類型、物件建立、未定義的值|  
|* / %|乘法、除法、modulo 除法|  
|+ - +|加法、減法、字串串連|  
|<\< >> >>>|位元移位|  
|< \<= > >= instanceof|小於、小於或等於、大於、大於或等於、instanceof|  
|== != === !==|等號比較、不等比較、嚴格等號比較和嚴格不等比較|  
|&|位元 AND|  
|^|位元 XOR|  
|&#124;|位元 OR|  
|&&|邏輯 AND|  
|&#124;&#124;|邏輯 OR|  
|?:|條件式|  
|= *OP*=|指派，以運算指派 (例如 += 和 &=)|  
|,|多重評估|  
  
 括號是用來改變以運算子優先順序決定的評估順序。 這表示在運算式的其餘部分使用這個值之前，會先完整評估括號內的運算式。  
  
 例如：  
  
```JavaScript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 第一個運算式中有三個運算子：=、* 和 +。 根據運算子優先順序的規則，它們的評估順序如下：\*、+、= (78 \* 96 = 7488、7488 + 3 = 7491)。  
  
 在第二個運算式中，會先評估 ( ) 運算子；因此，會先評估加法運算式再評估乘法 (9 + 3 = 12、12 * 78 = 936)。  
  
 下面範例會示範一個包含各種運算子並解析為 `true` 的陳述式。  
  
```JavaScript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 運算子的評估順序為：用於分組的 ( )、*、+ (位於群組內)、用於函式的 "."、用於函式的 ( )、/、==、=== 和 &&。