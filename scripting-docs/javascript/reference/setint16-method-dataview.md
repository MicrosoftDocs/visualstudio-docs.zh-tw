---
title: setInt16 方法 (DataView) |Microsoft 文件
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
ms.assetid: 901c6cf5-63fb-45bd-9ea8-185c1d892060
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04ea20079c217d1aeef8456e9c81996661fed356
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639398"
---
# <a name="setint16-method-dataview"></a>setInt16 方法 (DataView)
設定在指定的位元組位移的 Int16 值，從檢視的開始。 沒有對齊方式限制;多位元組值可能會設定任何位移。  
  
## <a name="syntax"></a>語法  
  
```  
dataView.setInt16(byteOffset, value, littleEndian);   
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
 下列範例會示範如何設定在 DataView 中的第一個 Int16。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt16(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]