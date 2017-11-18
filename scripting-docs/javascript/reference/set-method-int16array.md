---
title: "set 方法 (Int16Array) |Microsoft 文件"
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
ms.assetid: e35adfff-7052-4ef9-80be-3abbf8230e88
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 873dd12eb4b026118fdbdc03e29bc8dafca2a1aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-int16array"></a>set 方法 (Int16Array)
設定一個值或值陣列。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
int16Array.set(index, value);  
int16Array.set(array, offset);  
  
```  
  
## <a name="parameters"></a>參數  
 `index`  
 要設定之位置的索引。  
  
 `value`  
 要設定的值。  
  
 `array`  
 要設定之具類型或不具類型的值陣列。  
  
 `offset`  
 目前陣列中的索引，這些值將會寫入至這個位置。  
  
## <a name="remarks"></a>備註  
 如果輸入陣列是 TypedArray，則這兩個陣列可以使用相同的基礎 ArrayBuffer。 在這種情況下設定值時，就如同先將所有資料都複製到不與其中任何一個陣列重疊的暫存緩衝區，再將資料從暫存緩衝區複製到目前的陣列一般。  
  
 如果 offset 與指定的陣列長度總和超出目前 TypedArray 的範圍，就會引發例外狀況。  
  
## <a name="example"></a>範例  
 下列範例將示範如何設定陣列的第一個元素。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int16Array(buffer.byteLength / 2);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]