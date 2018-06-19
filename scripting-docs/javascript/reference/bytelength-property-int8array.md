---
title: byteLength 屬性 (Int8Array) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4e8457a8-2200-4d61-800e-f49fc1e916e5
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c50f49aa7fd9665214fe4269d36766c38891f309
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633828"
---
# <a name="bytelength-property-int8array"></a>byteLength 屬性 (Int8Array)
唯讀。 這個陣列從其 ArrayBuffer 開頭算起的長度 (以位元組為單位)，在建構階段長度都不會改變。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
var arrayByteLength = int8Array.byteLength;  
```  
  
## <a name="example"></a>範例  
 下列範例將示範如何取得陣列的長度。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            alert(intArr.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]