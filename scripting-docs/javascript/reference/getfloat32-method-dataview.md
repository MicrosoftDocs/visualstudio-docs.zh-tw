---
title: getFloat32 方法 (DataView) |Microsoft 文件
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
ms.assetid: adecf671-bde4-46be-a875-33b6d6e970b1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75fc5be6d8563a44504ae2d1c7ddd9429eccb390
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636498"
---
# <a name="getfloat32-method-dataview"></a>getFloat32 方法 (DataView)
從開始檢視中取得指定的位元組位移的 Float32 值。 沒有對齊方式限制;多位元組值可能會擷取從任何的位移。  
  
## <a name="syntax"></a>語法  
  
```  
var testFloat = dataView.getFloat32(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>參數  
 `testFloat`  
 必要項。 從方法傳回的 Float32 值。  
  
 `byteOffset`  
 值應該擷取的緩衝區中的位置。  
  
 `littleEndian`  
 選擇項。 如果為 false 或未定義，應該讀取的位元組由大到小的值，否則由小到大值應一併閱讀。  
  
## <a name="remarks"></a>備註  
 如果它們會讀取檢視結尾之外，這些方法會引發例外狀況。  
  
## <a name="example"></a>範例  
 下列範例會示範如何取得在 DataView 中的第一個 Float32。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat32(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]