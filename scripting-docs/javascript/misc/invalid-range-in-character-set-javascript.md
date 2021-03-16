---
description: 您嘗試使用不正確字元集範圍來建立正則運算式。
title: 字元集中的範圍無效 (JavaScript) |Microsoft 檔
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9441f9cfd3adf94ddd38841d522c83922c9154f1
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571671"
---
# <a name="invalid-range-in-character-set-javascript"></a>不正確的字元集範圍 (JavaScript)
您嘗試使用不正確字元集範圍來建立正則運算式。 字元集的範圍必須僅限單一字元，例如 a-z 或 0-9;字元類別（例如 \w）不能包含在字元集中。 範圍中的第一個字元也必須位於範圍中的第二個字元之前。 例如：  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請只使用單一字元來撰寫您的正則運算式字元集，並確定它們的順序正確。  
  
## <a name="see-also"></a>另請參閱  
 [正則運算式物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [ (JavaScript) 的正則運算式語法 ](/previous-versions/1400241x(v=vs.100))
