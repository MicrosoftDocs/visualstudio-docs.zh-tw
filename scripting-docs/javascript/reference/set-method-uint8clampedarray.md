---
title: set 方法 (Uint8ClampedArray) |Microsoft 文件
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
ms.assetid: 1298443d-5c4c-4329-9ad2-35e213dca157
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed7635559e615746c577560f1a9266b26acd959d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639468"
---
# <a name="set-method-uint8clampedarray"></a>set 方法 (Uint8ClampedArray)
設定一個值或值陣列。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
uint8ClampedArray.set(index, value);  
uint8ClampedArray.set(array, offset);  
  
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
 如果輸入的陣列的類型的陣列，則兩個陣列可以使用相同的基礎[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。 在這種情況下設定值時，就如同先將所有資料都複製到不與其中任何一個陣列重疊的暫存緩衝區，再將資料從暫存緩衝區複製到目前的陣列一般。  
  
 如果位移與指定的陣列長度總和超出目前類型陣列的範圍，就會引發例外狀況。  
  
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
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray 物件](../../javascript/reference/uint8clampedarray-object-javascript.md)