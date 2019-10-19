---
title: "' default ' 只可以在 ' switch ' 語句中出現一次 |Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90652e44a4bd0362f679be71d0d6401165487aec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572890"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' 只可以出現在 'switch' 陳述式中一次
您嘗試在 switch 語句中多次使用**default**語句。 預設案例一律為 switch 語句中的最後一個 case 語句（這是迴圈式案例）。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 從您的 `switch` 語句中移除任何額外的**預設**case 語句（在 switch 語句中最多使用一個預設 case 語句）。  
  
## <a name="see-also"></a>請參閱  
 [Switch 語句](../../javascript/reference/switch-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [JavaScript 保留字](../../javascript/reference/javascript-reserved-words.md)