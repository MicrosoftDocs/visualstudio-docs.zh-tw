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
ms.openlocfilehash: e1223b3cee7f0246d8d685260fb6ea9ad0045347
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817641"
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
  
## <a name="see-also"></a>另請參閱  
 [continue 語句](../../javascript/reference/continue-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
