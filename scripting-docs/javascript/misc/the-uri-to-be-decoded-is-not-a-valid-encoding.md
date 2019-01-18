---
title: 要解碼的 URI 不有效的編碼 |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344378"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>要解碼的 URI 不是有效的編碼
您嘗試解碼格式不正確的 URI （統一資源識別項）。 Uri 具有特殊語法;大部分的非英數字元必須編碼，才能在 URI 中使用。 您可以使用`encodeURI`並`encodeURIComponent`方法來建立 URI，從一般[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]字串。  
  
 完整的 URI 被組成一連串的元件和分隔符號。 一般格式如下：  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 角括弧括住的名稱代表的元件，而":"，"/"，";"和"？"是用來做為分隔符號的保留的字元。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定您嘗試解碼有效的 Uri。 您無法解碼一般[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]字串，因為它們可能包含無效的字元。  
  
## <a name="see-also"></a>另請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)