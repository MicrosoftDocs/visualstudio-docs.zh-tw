---
title: "' default ' 只可以在 ' switch ' 語句中出現一次 |Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: b49b5cfe7076a4a9504500a63f4d47d2f54bcc1a
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862786"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' 只可以出現在 'switch' 陳述式中一次
您嘗試在 switch 語句中多次使用 **default** 語句。 在 switch 語句中，預設的 case 一律是最後一個 case 語句 (它是) 。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 從您的語句移除任何額外的 **預設** case 語句 `switch` ， (在 switch 語句中最多使用一個預設的 case 語句) 。  
  
## <a name="see-also"></a>請參閱  
 [switch 語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/switch)   
 [控制程式流程](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [JavaScript 保留字](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)