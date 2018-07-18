---
title: 可以 &#39; 沒有 &#39; 中斷 &#39;迴圈外 |Microsoft 文件
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
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633148"
---
# <a name="can39t-have-39break39-outside-of-loop"></a>可以 &#39; 沒有 &#39; 中斷 &#39;迴圈外
您嘗試使用**中斷**迴圈外部的關鍵字。 **中斷**關鍵字用來終止迴圈或`switch`陳述式。 它必須在迴圈的主體中內嵌或`switch`陳述式。 不過，**標籤**可以依照 break 關鍵字。  
  
```  
break labelname;  
```  
  
 您只需要加上標籤的形式**中斷**關鍵字，當您使用巢狀迴圈或`switch`陳述式，且需要中斷不是最內層的迴圈。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定**中斷**封閉迴圈或 switch 陳述式內出現的關鍵字。  
  
## <a name="see-also"></a>另請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)