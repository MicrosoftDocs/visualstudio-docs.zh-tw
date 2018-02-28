---
title: "encodeURI 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- encodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURI method
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf9bbdf34c0481c889d1176bc32ab0246a333a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuri-function-javascript"></a>encodeURI 函式 (JavaScript)
將編碼的文字字串做為有效的統一資源識別元 (URI)  
  
## <a name="syntax"></a>語法  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## <a name="remarks"></a>備註  
 所需`URIString`引數是值，代表編碼的 URI。  
  
 `encodeURI`函式會傳回已編碼的 URI。 如果您將傳遞至結果`decodeURI`，就會傳回原始的字串。 `encodeURI`函式不會編碼下列字元:":"，"/"，";"和"？"。 使用`encodeURIComponent`編碼這些字元。  
  
## <a name="example"></a>範例  
 下列程式碼第一次編碼，並再將解碼的 URI。  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)