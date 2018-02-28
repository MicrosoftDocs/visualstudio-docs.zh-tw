---
title: "decodeURIComponent 函式 (JavaScript) |Microsoft 文件"
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
- decodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURIComponent method
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef7bdcd374a328bad632381d19e9823853d37f01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuricomponent-function-javascript"></a>decodeURIComponent 函式 (JavaScript)
取得解碼的編碼元件的統一資源識別元 (URI) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>備註  
 所需`encodedURIString`引數是代表編碼的 URI 元件的值。  
  
 URIComponent 是完整的 URI 的一部分。  
  
 如果`encodedURIString`不正確，就會發生 URIError。  
  
## <a name="example"></a>範例  
 下列程式碼第一次編碼，並再將解碼的 URI。  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)