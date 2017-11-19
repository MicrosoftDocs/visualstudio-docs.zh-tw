---
title: "setInt8 方法 (DataView) |Microsoft 文件"
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
ms.assetid: 0a0e1450-e0c4-4778-8706-4d332442d882
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6f9bd9c4b3bea25686036d199d1a987927172d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="setint8-method-dataview"></a>setInt8 方法 (DataView)
儲存在指定的位元組位移，從開始檢視的 Int8 值。  
  
## <a name="syntax"></a>語法  
  
```  
dataView.setInt8(byteOffset, value);   
```  
  
## <a name="parameters"></a>參數  
 `byteOffset`  
 中的值應該設定的緩衝區位置。  
  
 `value`  
 要設定的值。  
  
## <a name="remarks"></a>備註  
 如果它們撰寫檢視的結尾之外，這些方法會引發例外狀況。  
  
## <a name="example"></a>範例  
 下列範例會示範如何設定在 DataView 中的第一個 Int8。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt8(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]