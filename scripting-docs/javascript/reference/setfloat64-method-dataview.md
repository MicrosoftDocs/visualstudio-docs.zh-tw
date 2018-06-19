---
title: setFloat64 方法 (DataView) |Microsoft 文件
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
ms.assetid: 63d2c631-876f-4d4b-b3b6-62b0aaffe6c5
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e22552e4190c74b520dfce853be6e9d1364764e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639958"
---
# <a name="setfloat64-method-dataview"></a>setFloat64 方法 (DataView)
設定在指定的位元組位移的 Float64 值，從檢視的開始。 沒有對齊方式限制;多位元組值可能會設定任何位移。  
  
## <a name="syntax"></a>語法  
  
```  
dataView.setFloat64 (byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>參數  
 `byteOffset`  
 值應該擷取的緩衝區中的位置。  
  
 `value`  
 要設定的值。  
  
 `littleEndian`  
 選擇項。 如果為 false，或未定義，應寫入的位元組由大到小的值，否則應該寫入由小到大值。  
  
## <a name="remarks"></a>備註  
 如果它們撰寫檢視的結尾之外，這些方法會引發例外狀況。  
  
## <a name="example"></a>範例  
 下列範例會示範如何設定在 DataView 中的第一個 Float64。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat64(0, 9.1);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]