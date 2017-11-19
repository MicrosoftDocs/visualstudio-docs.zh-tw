---
title: "Float64Array 物件 |Microsoft 文件"
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
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20544812d94c1234d85d714f6e469d0de4f4c5ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="float64array-object"></a>Float64Array 物件
64 位元浮點值的類型陣列。 內容已初始化為 0。 如果無法配置要求的位元組數目，就會引發例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
  
      float64Array = new Float64Array( length );  
float64Array = new Float64Array( array );  
float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>參數  
 `float64Array`  
 必要項。 變數名稱的**Float64Array**指派給物件。  
  
 `length`  
 指定陣列中元素的數目。  
  
 `array`  
 這個陣列中所包含的陣列 (或類型陣列)。 內容會初始化為所指陣列或類型陣列的內容，其中每個元素都會轉換成 Float64 類型。  
  
 `buffer`  
 Float64Array 代表的 ArrayBuffer。  
  
 `byteOffset`  
 選擇項。 以位元組為單位，指定從緩衝區開頭 (也就是 Float64Array 應該開始的位置) 算起的位移。  
  
 `length`  
 陣列中的元素數目。  
  
## <a name="constants"></a>常數  
 下表列出 `Float64Array` 物件的常數。  
  
|常數|說明|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT 常數](../../javascript/reference/bytes-per-element-constant-float64array.md)|陣列中每個元素的大小 (以位元組為單位)。|  
  
## <a name="properties"></a>屬性  
 下表列出 `Float64Array` 物件的常數。  
  
|屬性|說明|  
|--------------|-----------------|  
|[buffer 屬性](../../javascript/reference/bytelength-property-float64array.md)|唯讀。 取得這個陣列所參考的 ArrayBuffer。|  
|[byteLength 屬性](../../javascript/reference/bytelength-property-float64array.md)|唯讀。 這個陣列從其 ArrayBuffer 開頭算起的長度 (以位元組為單位)，在建構階段長度都不會改變。|  
|[byteOffset 屬性](../../javascript/reference/length-property-float64array.md)|唯讀。 這個陣列從其 ArrayBuffer 開頭算起的位移 (以位元組為單位)，在建構階段位移都不會改變。|  
|[length 屬性](../../javascript/reference/length-property-float64array.md)|陣列的長度。|  
  
## <a name="methods"></a>方法  
 下表列出 `Float64Array` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[get 方法](../../javascript/reference/get-method-float64array.md)|可省略。 取得位在指定索引處的項目。|  
|[set 方法 (Float64Array)](../../javascript/reference/set-method-float64array.md)|設定一個值或值陣列。|  
|[subarray 方法 (Float64Array)](../../javascript/reference/subarray-method-float64array.md)|為這個陣列取得 ArrayBuffer 存放區的新 Float64Array 檢視。|  
  
## <a name="example"></a>範例  
 下列範例將示範如何使用 Float64Array 物件處理從 XmlHttpRequest 取得的二進位資料：  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float64Array(buffer.byteLength / 8);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat64(i * 8);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]