---
title: subarray 方法 (Uint8ClampedArray) |Microsoft 文件
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cda8b123b02b4c19a7fd162f3bfbce4540d149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640548"
---
# <a name="subarray-method-uint8clampedarray"></a>subarray 方法 (Uint8ClampedArray)
取得新[Uint8ClampedArray](../../javascript/reference/uint8array-object.md)檢視[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)儲存為這個陣列，指定子陣列的第一個和最後一個成員。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## <a name="parameters"></a>參數  
 `newUint8ClampedArray`  
 必要項。 這個方法所傳回的子陣列。  
  
 `begin`  
 選擇項。 陣列開頭的索引。  
  
 `end`  
 選擇項。 陣列結尾的索引。 這個索引為非內含。  
  
## <a name="remarks"></a>備註  
 如果 `begin` 或 `end` 是負值，則是指從陣列結尾起算的索引，而非從開頭起算。 如果未指定 `end`，子陣列就會包含從類型陣列的 `begin` 到結尾的所有元素。 `begin` 和 `end` 值所指定的範圍僅限於目前陣列的有效索引範圍。 如果新的類型陣列的長度計算後為負值，則會限於零。 傳回的陣列與叫用這個方法的陣列具有相同類型。  
  
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
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Uint8Array 物件](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray 物件](../../javascript/reference/uint8clampedarray-object-javascript.md)