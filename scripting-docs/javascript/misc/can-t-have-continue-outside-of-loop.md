---
title: 迴圈外不可以有 ' continue ' |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: e19c85baf8576d1c1db411146c80a53c6a819cdb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572375"
---
# <a name="cant-have-continue-outside-of-loop"></a>迴圈外不可以有 'continue'
您嘗試在迴圈外使用**continue**語句。 **Continue**語句只能在的主體內使用：  
  
- `do-while` 迴圈，  
  
- `while` 迴圈，  
  
- **for**迴圈，  
  
- **for/in**迴圈。  
  
### <a name="to-correct-this-error"></a>若要改正這項錯誤  
  
- 請確定**continue**語句出現在的主體內：  
  
  - `do-while` 迴圈，  

  - `while` 迴圈，  

  - **for**迴圈，  

  - **for/in**迴圈。  
  
## <a name="see-also"></a>另請參閱  
 [Continue 語句](../../javascript/reference/continue-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
