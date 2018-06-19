---
title: encodeURIComponent 函式 (JavaScript) |Microsoft 文件
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
- encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636428"
---
# <a name="encodeuricomponent-function-javascript"></a>encodeURIComponent 函式 (JavaScript)
編碼的文字字串做為有效的元件的統一資源識別元 (URI)。  
  
## <a name="syntax"></a>語法  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>備註  
 所需`encodedURIString`引數是代表編碼的 URI 元件的值。  
  
 `encodeURIComponent`函式會傳回已編碼的 URI。 如果您將傳遞至結果`decodeURIComponent`，就會傳回原始的字串。 因為`encodeURIComponent`函式會將所有的字元編碼，請格外小心，如果字串代表路徑例如 **/folder1/folder2/default.html**。 斜線字元必須編碼，而且不會做為要求傳送至 web 伺服器，才有效。 使用`encodeURI`函式，如果字串包含多個單一的 URI 元件。  
  
## <a name="example"></a>範例  
 下列程式碼會先編碼 URI 元件，並再將它解碼。  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)