---
title: 不可以有 'break' 迴圈外 |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53f32da997b775e01959df5abc7e72fb55c1b194
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086693"
---
# <a name="cant-have-break-outside-of-loop"></a>迴圈外不可以有 'break'
您嘗試使用**中斷**迴圈外的關鍵字。 **中斷**關鍵字用來終止迴圈或`switch`陳述式。 它必須在迴圈的主體中內嵌或`switch`陳述式。 不過，**標籤**可以依照 break 關鍵字。  
  
```js
break labelname;  
```  
  
 您只需要加上標籤的形式**中斷**關鍵字，當您使用巢狀迴圈或`switch`陳述式和不必中斷並不是最內層的迴圈。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定**中斷**關鍵字會出現在封閉式迴圈或 switch 陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)