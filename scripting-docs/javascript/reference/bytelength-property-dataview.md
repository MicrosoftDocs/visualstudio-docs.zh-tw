---
title: "byteLength 屬性 (DataView) |Microsoft 文件"
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
ms.assetid: 6274285f-b673-48f6-a1e7-89ff7ee348b5
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2a9eb55a40722c42ccc9711c434061e98b64039
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="bytelength-property-dataview"></a>byteLength 屬性 (DataView)
唯讀。 這個檢視從其 ArrayBuffer 開頭算起的長度 (以位元組為單位)，在建構階段長度都不會改變。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
var byteLength = dataView.byteLength;  
```  
  
## <a name="example"></a>範例  
 下列範例將示範如何從 XMLHttpRequest 取得 DataView 的長度。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]