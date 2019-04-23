---
title: "'default' 只能在 'switch' 陳述式中一次出現 |Microsoft Docs"
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
ms.openlocfilehash: 24162efcc720d9c0073f8a5799c6278b8d3c8c62
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107823"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' 只可以出現在 'switch' 陳述式中一次
您嘗試使用**預設**不止一次在 switch 陳述式內的陳述式。 預設的情況中一律是 switch 陳述式 （它是 fall-through 大小寫） 中的最後一個 case 陳述式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 移除任何額外**預設**case 陳述式，從您`switch`陳述式 （在大部分的一個預設 case 陳述式，您的 switch 陳述式中使用）。  
  
## <a name="see-also"></a>另請參閱  
 [switch 陳述式](../../javascript/reference/switch-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [JavaScript 保留字](../../javascript/reference/javascript-reserved-words.md)