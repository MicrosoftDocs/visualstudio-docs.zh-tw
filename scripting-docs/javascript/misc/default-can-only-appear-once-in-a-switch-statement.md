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
ms.openlocfilehash: a5d31a74900e8eee5daa97bb7f9af5146b237e04
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842178"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' 只可以出現在 'switch' 陳述式中一次
您嘗試使用**預設**不止一次在 switch 陳述式內的陳述式。 預設的情況中一律是 switch 陳述式 （它是 fall-through 大小寫） 中的最後一個 case 陳述式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除任何額外**預設**case 陳述式，從您`switch`陳述式 （在大部分的一個預設 case 陳述式，您的 switch 陳述式中使用）。  
  
## <a name="see-also"></a>另請參閱  
 [switch 陳述式](../../javascript/reference/switch-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [JavaScript 保留字](../../javascript/reference/javascript-reserved-words.md)