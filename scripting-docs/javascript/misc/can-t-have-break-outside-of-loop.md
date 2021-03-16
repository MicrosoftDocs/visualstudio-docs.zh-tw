---
description: 您嘗試在迴圈之外使用 break 關鍵字。
title: 迴圈外不可以有 ' break ' |Microsoft 檔
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: d761a1cff89f650e5fc465b6a6aef2713aafb765
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570644"
---
# <a name="cant-have-break-outside-of-loop"></a>迴圈外不可以有 'break'
您嘗試在迴圈之外使用 **break** 關鍵字。 **Break** 關鍵字是用來終止迴圈或 `switch` 語句。 它必須內嵌在迴圈或語句的主體中 `switch` 。 不過， **標籤** 可以跟隨 break 關鍵字。  
  
```js
break labelname;  
```  
  
 當您使用嵌套迴圈或 `switch` 語句，且需要中斷非最內層的迴圈時，您只需要標記形式的 break 關鍵字。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定 **break** 關鍵字出現在封閉式迴圈或 switch 語句內。  
  
## <a name="see-also"></a>另請參閱  
 [break 語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [控制程式流程](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [指令碼疑難排解](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)
