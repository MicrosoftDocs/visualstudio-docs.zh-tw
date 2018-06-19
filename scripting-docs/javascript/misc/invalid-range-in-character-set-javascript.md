---
title: 不正確的字元範圍設定 (JavaScript) |Microsoft 文件
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
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14d0d5ddf282c6994c572668136e6d7283794f6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632998"
---
# <a name="invalid-range-in-character-set-javascript"></a>不正確的字元集範圍 (JavaScript)
您嘗試使用無效的字元設定的範圍建立規則運算式。 字元集必須在範圍內從單一字元，例如 a 到 z 或 0-9;您不能包含字元類別，例如 \w 字元集中。 也必須在範圍中的第一個字元前面範圍的第二個字元。 例如：  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用只能有單一字元，來撰寫規則運算式字元設定，並確定它們依正確順序。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)