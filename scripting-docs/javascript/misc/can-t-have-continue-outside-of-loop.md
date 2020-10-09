---
title: 迴圈外不可以有 ' continue ' |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d2d95259-b2bc-4069-9876-60c30ad600a3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14745c5789fe6c0350f83e46ee0e918f92789d96
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861984"
---
# <a name="cant-have-continue-outside-of-loop"></a>迴圈外不可以有 'continue'
您嘗試在迴圈外使用 **continue** 語句。 **Continue**語句只能用在的主體內：  
  
- `do-while` 環  
  
- `while` 環  
  
- **for** 迴圈  
  
- **for/in** 迴圈。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定 **continue** 語句出現在的主體內：  
  
  - `do-while` 環  

  - `while` 環  

  - **for** 迴圈  

  - **for/in** 迴圈。  
  
## <a name="see-also"></a>請參閱  
 [continue 語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/continue)   
 [控制程式流程](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [指令碼疑難排解](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)