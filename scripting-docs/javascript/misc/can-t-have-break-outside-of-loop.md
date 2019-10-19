---
title: 迴圈外不可以有 ' break ' |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 356e7022f940e696030b0cda4f71a599c147dd5a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576023"
---
# <a name="cant-have-break-outside-of-loop"></a>迴圈外不可以有 'break'
您嘗試在迴圈外使用**break**關鍵字。 **Break**關鍵字用來結束迴圈或 `switch` 語句。 它必須內嵌在迴圈或 `switch` 語句的主體中。 不過，**標籤**可以跟隨 break 關鍵字。  
  
```js
break labelname;  
```  
  
 當您使用嵌套迴圈或 `switch` 語句，而且需要中斷不是最內層的迴圈時，您只需要有標記形式的**break**關鍵字。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定**break**關鍵字出現在封閉式迴圈或 switch 語句內。  
  
## <a name="see-also"></a>請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)