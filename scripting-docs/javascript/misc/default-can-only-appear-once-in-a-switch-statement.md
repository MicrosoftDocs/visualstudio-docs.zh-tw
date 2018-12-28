---
title: "'default' 只能在 'switch' 陳述式中一次出現 |Microsoft Docs"
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
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4f254825e27793999932b772ac4bc2512908fae
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803879"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' 只可以出現在 'switch' 陳述式中一次
您嘗試使用**預設**不止一次在 switch 陳述式內的陳述式。 預設的情況中一律是 switch 陳述式 （它是 fall-through 大小寫） 中的最後一個 case 陳述式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除任何額外**預設**case 陳述式，從您`switch`陳述式 （在大部分的一個預設 case 陳述式，您的 switch 陳述式中使用）。  
  
## <a name="see-also"></a>另請參閱  
 [switch 陳述式](../../javascript/reference/switch-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [JavaScript 保留字](../../javascript/reference/javascript-reserved-words.md)