---
title: 預期的 VBArray |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b4e6521e5d363c21311b19e2ecc1679981acac3
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862700"
---
# <a name="vbarray-expected"></a>必須是 VBArray
您提供了一個不是 Visual Basic safeArray 的物件（如果預期的話）。  
  
```js
new VBArray(safeArray);  
```  
  
 VBArray 是唯讀的，而且無法直接建立。 SafeArray 引數是 VBArray 值，而且必須先取得 VBArray 值，才能傳遞至函式 `VBArray` 。 您只能從現有的 ActiveX 或其他物件中擷取此值，來達到這個目的。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 確定您只將 **VBArray** 物件傳遞至 **VBArray** 的函式。  
  
## <a name="see-also"></a>請參閱  
 [VBArray 物件](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [使用陣列](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)