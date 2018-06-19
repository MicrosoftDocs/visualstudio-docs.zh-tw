---
title: decodeURI 函式 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636238"
---
# <a name="decodeuri-function-javascript"></a>decodeURI 函式 (JavaScript)
取得未編碼的版本的編碼統一資源識別元 (URI)。  
  
## <a name="syntax"></a>語法  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>備註  
 所需`URIstring`引數是值，代表編碼的 URI。  
  
 使用`decodeURI`函式，而不是已被取代`unescape`函式。  
  
 `decodeURI`函式會傳回字串值。  
  
 如果`URIString`不正確，就會發生 URIError。  
  
 **適用於**:[全域物件](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>範例  
 下列程式碼會先編碼 URI 元件，並再將它解碼。  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)   
 [Global 物件](../../javascript/reference/global-object-javascript.md)