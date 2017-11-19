---
title: "ArrayBuffer 物件 |Microsoft 文件"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="arraybuffer-object"></a>ArrayBuffer 物件
代表二進位資料的原始緩衝區，用來儲存不同類型陣列的資料。 `ArrayBuffers`無法讀取或寫入直接，但是可以傳遞給類型陣列或[DataView 物件](../../javascript/reference/dataview-object.md)來視需要解譯原始緩衝區。  
  
 如需具類型陣列的詳細資訊，請參閱[別陣列](../../javascript/advanced/typed-arrays-javascript.md)。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>參數  
 `arrayBuffer`  
 必要項。 要對其指派 `ArrayBuffer` 物件的變數名稱。  
  
 `length`  
 緩衝區的長度。 ArrayBuffer 的內容已初始化為 0。 如果無法配置要求的位元組數目，就會引發例外狀況。  
  
## <a name="properties"></a>屬性  
 下表列出 `ArrayBuffer` 物件的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[byteLength 屬性](../../javascript/reference/bytelength-property-arraybuffer.md)|唯讀。 ArrayBuffer 的長度 (以位元組為單位)。|  
  
## <a name="functions"></a>函式  
 下表列出 `ArrayBuffer` 物件的函式。  
  
|屬性|說明|  
|--------------|-----------------|  
|[ArrayBuffer.isView 函式](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|決定物件是否提供緩衝區的檢視。|  
  
## <a name="methods"></a>方法  
 下表列出 `ArrayBuffer` 物件的方法。  
  
|屬性|說明|  
|--------------|-----------------|  
|[slice 方法](../../javascript/reference/slice-method-arraybuffer.md)|傳回 `ArrayBuffer` 的一個區段。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 ArrayBuffer 物件來處理從取得的二進位資料[XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx)。 您可以使用[DataView 物件](../../javascript/reference/dataview-object.md)取得個別值。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="remarks"></a>備註  
 如需有關使用`XmlHttpRequest`，請參閱[XMLHttpRequest 增強功能](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069)。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]