---
title: "subarray 方法 (Uint32Array) |Microsoft 文件"
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
ms.assetid: 4c183208-12ec-4051-bf0f-a4f7c112cea1
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1c76c5c83bcb1e43b51b4f49618e72311d5df86
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint32array"></a>subarray 方法 (Uint32Array)
取得的新 Uint32Array 檢視[ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)儲存為這個陣列，指定子陣列的第一個和最後一個成員。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
var newUint32Array = uint32Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>參數  
 `newUint32Array`  
 這個方法所傳回的子陣列。  
  
 `begin`  
 陣列開頭的索引。  
  
 `end`  
 陣列結尾的索引。 這個索引為非內含。  
  
## <a name="remarks"></a>備註  
 如果 `begin` 或 `end` 是負值，則是指從陣列結尾起算的索引，而非從開頭起算。 如果未指定 `end`，子陣列就會包含從類型陣列的 `begin` 到結尾的所有元素。 `begin` 和 `end` 值所指定的範圍僅限於目前陣列的有效索引範圍。 如果新的類型陣列的長度計算後為負值，則會限於零。 傳回的陣列與叫用這個方法的陣列會屬於相同類型。  
  
## <a name="example"></a>範例  
 下列範例將示範如何從來源陣列的第一個元素開始，取得包含兩個元素的子陣列。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]