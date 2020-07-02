---
title: 需要 VBArray |Microsoft Docs
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
ms.openlocfilehash: 09ab257e6c473e2747a24559200e7b1f432d5687
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815275"
---
# <a name="vbarray-expected"></a>必須是 VBArray
您提供了一個不是 Visual Basic safeArray 的物件（如果有的話）。  
  
```js
new VBArray(safeArray);  
```  
  
 VBArray 是唯讀的，而且無法直接建立。 SafeArray 引數是 VBArray 值，必須先取得 VBArray 值，才能傳遞給此函式 `VBArray` 。 您只能從現有的 ActiveX 或其他物件中擷取此值，來達到這個目的。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定您只將**VBArray**物件傳遞至**VBArray**的函式。  
  
## <a name="see-also"></a>另請參閱  
 [VBArray 物件](../../javascript/reference/vbarray-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)