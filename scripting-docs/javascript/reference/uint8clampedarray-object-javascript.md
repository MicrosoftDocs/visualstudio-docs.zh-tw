---
title: Uint8ClampedArray 物件 (JavaScript) |Microsoft 文件
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51673eadc8eb905355bf136dc82b2f240462180a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642108"
---
# <a name="uint8clampedarray-object-javascript"></a>Uint8ClampedArray 物件 (JavaScript)
8 位元不帶正負號整數 (值壓制為範圍 0-255) 的類型陣列。 內容已初始化為 0。 如果無法配置要求的位元組數目，就會擲回例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
  
      uint8ClampedArray = new Uint8ClampedArray( length );  
uint8ClampedArray = new Uint8ClampedArray( array );  
uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>參數  
 `uint8ClampedArray`  
 必要項。 要對其指派 `Uint8ClampedArray` 物件的變數名稱。  
  
 `length`  
 選擇項。 陣列中的元素數目。  
  
 `array`  
 選擇項。 這個陣列中所包含的陣列 (或類型陣列)。 內容會初始化為所指定陣列或類型陣列的內容，其中每個項目都會轉換成 `Uint8` 類型。  
  
 `buffer`  
 選擇項。 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) ，`Uint8ClampedArray`代表。  
  
 `byteOffset`  
 選擇項。 從緩衝區開頭 (也就是 `Uint8ClampedArray` 應該開始的位置) 算起的位移 (以位元組為單位)。  
  
 `length`  
 選擇項。 陣列中的項目數。  
  
## <a name="remarks"></a>備註  
 `Uint8ClampedArray` 物件中所儲存的值介於 0 與 255 之間。 如果您將陣列成員設為負值，則會將值設為 0。 如果您設定的值大於 255，則會將值設為 255。  
  
 中的值`Uint8ClampedArray`物件四捨五入到最接近的偶數值，稱為成雙。  
  
## <a name="constants"></a>常數  
 下表列出 `Uint8ClampedArray` 物件的常數。  
  
|常數|說明|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT 常數](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|陣列中每個項目的大小 (以位元組為單位)。|  
  
## <a name="properties"></a>屬性  
 下表列出 `Uint8ClampedArray` 物件的常數。  
  
|屬性|說明|  
|--------------|-----------------|  
|[buffer 屬性](../../javascript/reference/buffer-property-uint8clampedarray.md)|唯讀。 取得[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)這個陣列所參考。|  
|[byteLength 屬性](../../javascript/reference/bytelength-property-uint8clampedarray.md)|唯讀。 從開始，這個陣列的長度其[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)，以位元組為單位，因為在建構階段。|  
|[byteOffset 屬性](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|唯讀。 這個陣列從開頭的位移其[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)，以位元組為單位，因為在建構階段。|  
|[length 屬性](../../javascript/reference/length-property-uint8clampedarray.md)|陣列的長度。|  
  
## <a name="methods"></a>方法  
 下表列出 `Uint8ClampedArray` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[set 方法](../../javascript/reference/set-method-uint8clampedarray.md)|設定一個值或值陣列。|  
|[subarray 方法](../../javascript/reference/subarray-method-uint8clampedarray.md)|取得新`Uint8ClampedArray`檢視[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)儲存為這個陣列，指定子陣列的第一個和最後一個項目。|  
  
## <a name="example"></a>範例  
 下列範例將示範如何使用 `Uint8ClampedArray` 物件處理從 `XmlHttpRequest` 取得的二進位資料：  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="example"></a>範例  
 下列範例顯示值在 `Uint8ClampedArray` 中的限制方式。  
  
```JavaScript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## <a name="example"></a>範例  
 下列範例顯示值在 `Uint8ClampedArray` 中的四捨五入方式。  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 12 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Uint8Array 物件](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)
