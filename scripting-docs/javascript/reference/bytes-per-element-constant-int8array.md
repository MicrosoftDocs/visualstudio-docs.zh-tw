---
title: "BYTES_PER_ELEMENT 常數 (Int8Array) |Microsoft 文件"
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
ms.assetid: 1b363d53-6190-4419-bb33-fe4a3a5fab05
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d181adb6ac26b4a3055ee946e27c4052d4e1c3de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="bytesperelement-constant-int8array"></a>BYTES_PER_ELEMENT 常數 (Int8Array)
陣列中每個元素的大小 (以位元組為單位)。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
var arraySize = int8Array.BYTES_PER_ELEMENT;  
```  
  
## <a name="example"></a>範例  
 下列範例將示範如何取得陣列元素的大小。  
  
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
            alert(intArr.BYTES_PER_ELEMENT);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]