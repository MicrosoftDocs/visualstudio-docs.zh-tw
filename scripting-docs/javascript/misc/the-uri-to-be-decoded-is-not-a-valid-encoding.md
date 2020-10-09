---
title: 要解碼的 URI 不是有效的編碼方式 |Microsoft Docs
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
ms.openlocfilehash: 38ea642cece501804b6ee2efaac778c3b8d520fc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861859"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>要解碼的 URI 不是有效的編碼
您嘗試將格式不正確的 URI 解碼 (統一資源識別項) 。 Uri 具有特殊語法;大部分的非英數位元必須先經過編碼，才能用於 URI 中。 您可以使用 `encodeURI` 和 `encodeURIComponent` 方法，從一般字串建立 URI [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 。  
  
 完整的 URI 是由一系列的元件和分隔符號所組成。 一般形式為：  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 角括弧中的名稱代表元件，而 "："、"/"、";" 和 "？" 是用來做為分隔符號的保留字元。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 確定您嘗試只將有效的 Uri 解碼。 您無法解碼一般 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 字串，因為它們可能包含不正確字元。  
  
## <a name="see-also"></a>請參閱  
 [decodeURI 函式](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuri)   
 [decodeURIComponent 函式](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuricomponent)