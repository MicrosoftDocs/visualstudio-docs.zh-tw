---
title: "byteLength 屬性 (Float64Array) |Microsoft 文件"
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
ms.assetid: 892498c1-dd6c-4037-89c2-cae29f5d09f2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 594f2f4b0baca773561f7527b673916a102f50e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="bytelength-property-float64array"></a>byteLength 屬性 (Float64Array)
唯讀。 這個陣列從其 ArrayBuffer 開頭算起的長度 (以位元組為單位)，在建構階段長度都不會改變。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
var arrayByteLength = float64Array.byteLength;  
```  
  
## <a name="example"></a>範例  
 下列範例會示範如何取得陣列的位元組長度。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            alert(floatArr.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]