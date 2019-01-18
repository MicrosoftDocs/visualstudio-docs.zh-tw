---
title: 必須是 VBArray |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4b5416c6e37e59a60206bd21606b5214f05a269
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347451"
---
# <a name="vbarray-expected"></a>必須是 VBArray
您提供不是 Visual Basic 的 safeArray，當一個預期的物件。  
  
```js
new VBArray(safeArray);  
```  
  
 VBArray 是唯讀的，而且無法直接建立。 SafeArray 引數是 VBArray 值，而且必須取得 VBArray 值，才會傳遞至`VBArray`建構函式。 您只能從現有的 ActiveX 或其他物件中擷取此值，來達到這個目的。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定您只傳遞**VBArray**物件至**VBArray**建構函式。  
  
## <a name="see-also"></a>另請參閱  
 [VBArray 物件](../../javascript/reference/vbarray-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)