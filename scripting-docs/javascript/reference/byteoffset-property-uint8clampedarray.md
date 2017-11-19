---
title: "byteOffset 屬性 (Uint8ClampedArray) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: bfc22cf4-00e3-4e2c-8419-032b179aa8da
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7997c90f59796f519cdeb4cab3f88965539d460b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="byteoffset-property-uint8clampedarray"></a>byteOffset 屬性 (Uint8ClampedArray)
唯讀。 這個陣列從開頭的位移其[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)，以位元組為單位，因為在建構階段。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
var arrayOffset = uint8ClampedArray.byteOffset;  
```  
  
## <a name="example"></a>範例  
 下列範例顯示如何取得陣列的位移。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray 物件](../../javascript/reference/uint8clampedarray-object-javascript.md)