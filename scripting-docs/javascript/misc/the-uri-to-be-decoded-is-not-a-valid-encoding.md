---
title: 要解碼的 URI 不是有效的編碼 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 98d2ee08a52e86c435c58502da1ab4f68b594905
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816159"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>要解碼的 URI 不是有效的編碼
您嘗試將格式不正確的 URI （統一資源識別項）解碼。 Uri 具有特殊語法;大部分的非英數位元都必須先進行編碼，才能在 URI 中使用。 您可以使用 `encodeURI` 和 `encodeURIComponent` 方法，從一般字串建立 URI [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 。  
  
 完整的 URI 是由一系列的元件和分隔符號所組成。 一般的形式如下：  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 角括弧中的名稱代表元件，而 "："、"/"、";" 和 "？" 是用來做為分隔符號的保留字元。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定您只嘗試解碼有效的 Uri。 您無法將一般 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 字串解碼，因為它們可能包含不正確字元。  
  
## <a name="see-also"></a>另請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)