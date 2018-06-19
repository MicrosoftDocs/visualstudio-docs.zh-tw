---
title: slice 方法 (ArrayBuffer) |Microsoft 文件
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640488"
---
# <a name="slice-method-arraybuffer"></a>slice 方法 (ArrayBuffer)
傳回的一個區段[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。  
  
## <a name="syntax"></a>語法  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>參數  
 `arrayBufferObj`  
 必要項。 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) > 一節將會從複製的物件。  
  
 `start`  
 必要項。 要複製之區段開頭的位元組索引。  
  
 `end`  
 選擇項。 要複製之區段結尾的位元組索引。  
  
## <a name="remarks"></a>備註  
 `slice`方法會傳回[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)物件，其中包含的指定的部分`arrayBufferObj`。  
  
 `slice` 方法會複製到 (但不含) `end` 所指出的位元組。 如果`start`或`end`是負數，指定的索引會被視為`length`  +  `start`或`end`分別其中`length`段[ArrayBuffer](../../javascript/reference/arraybuffer-object.md). 如果省略 `end`，則會一直擷取到 `arrayBufferObj` 的結尾。 如果`end`之前發生`start`，不會將位元組複製到新[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用 `slice` 方法。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)