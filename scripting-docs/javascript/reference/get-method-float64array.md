---
title: get 方法 (Float64Array) |Microsoft 文件
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
ms.assetid: debbe2f4-fe1e-4f9d-af7d-b24430bfa962
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bee0ffe2417c8cc2743f9fd35d74899a940dde6e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636478"
---
# <a name="get-method-float64array"></a>get 方法 (Float64Array)
可省略。 取得位在指定索引處的項目。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
var value = float64Array.get(index);  
```  
  
## <a name="parameters"></a>參數  
 `value`  
 這個方法傳回的值。  
  
 `index`  
 要取得之陣列元素所在的索引位置。  
  
## <a name="example"></a>範例  
 下列範例將示範如何取得陣列的第一個元素。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 4);  
            var element = floatArr.getFloat64(0);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]