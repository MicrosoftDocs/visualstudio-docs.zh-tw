---
title: 要解碼的 URI 不有效的編碼 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8fd8add72d016bc3f2e815f41c29c735505c8817
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006217"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>要解碼的 URI 不是有效的編碼
您嘗試解碼格式不正確的 URI （統一資源識別項）。 Uri 具有特殊語法;大部分的非英數字元必須編碼，才能在 URI 中使用。 您可以使用`encodeURI`並`encodeURIComponent`方法來建立 URI，從一般[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]字串。  
  
 完整的 URI 被組成一連串的元件和分隔符號。 一般格式如下：  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 角括弧括住的名稱代表的元件，而":"，"/"，";"和"？"是用來做為分隔符號的保留的字元。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定您嘗試解碼有效的 Uri。 您無法解碼一般[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]字串，因為它們可能包含無效的字元。  
  
## <a name="see-also"></a>另請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)