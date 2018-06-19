---
title: DataView 物件 |Microsoft 文件
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370ee1afbdf7fe1d87843c4979833d54a575a4fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637268"
---
# <a name="dataview-object"></a>DataView 物件
您可以使用 DataView 物件來讀取和寫入不同類型的二進位資料至 ArrayBuffer 中的任何位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## <a name="parameters"></a>參數  
 `dataView`  
 必要項。 變數名稱的**DataView**指派給物件。  
  
 `buffer`  
 DataView 所代表的 ArrayBuffer。  
  
 `byteOffset`  
 選擇項。 指定的位移，以位元組為單位，從開頭應該開始 DataView 的緩衝區。  
  
 `byteLength`  
 選擇項。 指定應該代表 DataView 的緩衝區之區段的長度 （以位元組為單位）。  
  
## <a name="remarks"></a>備註  
 如果省略了 byteOffset 和 byteLength DataView 跨越整個 ArrayBuffer 範圍。 如果省略 byteLength DataView 擴充來自 teradata 給定 byteOffset ArrayBuffer 的結尾。 如果給定的 byteOffset 和 byteLength 參考的 ArrayBuffer 結尾之外的區域，則會引發例外狀況。  
  
## <a name="properties"></a>屬性  
 下表列出 `DataView` 物件的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[buffer 屬性](../../javascript/reference/buffer-property-dataview.md)|唯讀。 取得這個檢視所參考的 ArrayBuffer。|  
|[byteLength 屬性](../../javascript/reference/bytelength-property-dataview.md)|唯讀。 這個檢視從其 ArrayBuffer 開頭算起的長度 (以位元組為單位)，在建構階段長度都不會改變。|  
|[byteOffset 屬性](../../javascript/reference/byteoffset-property-dataview.md)|唯讀。 這個檢視從其 ArrayBuffer，以位元組為單位，因為在建構階段的開始位移。|  
  
## <a name="methods"></a>方法  
 下表列出 `DataView` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[getInt8 方法](../../javascript/reference/getint8-method-dataview.md)|從開始檢視中取得指定的位元組位移的 Int8 值。|  
|[getUint8 方法 (DataView)](../../javascript/reference/getuint8-method-dataview.md)|從開始檢視中取得指定的位元組位移的 Uint8 值。|  
|[getInt16 方法 (DataView)](../../javascript/reference/getint16-method-dataview.md)|取得在指定的位元組位移的 Int16 值，從檢視的開始。|  
|[getUint16 方法 (DataView)](../../javascript/reference/getuint16-method-dataview.md)|從開始檢視中取得指定的位元組位移的 Uint16 值。|  
|[getInt32 方法 (DataView)](../../javascript/reference/getint32-method-dataview.md)|取得在指定的位元組位移的 Int32 值，從檢視的開始。|  
|[getUint32 方法 (DataView)](../../javascript/reference/getuint32-method-dataview.md)|取得在指定的位元組位移的 Uint32 值，從檢視的開始。|  
|[getFloat32 方法 (DataView)](../../javascript/reference/getfloat32-method-dataview.md)|從開始檢視中取得指定的位元組位移的 Float32 值。|  
|[getFloat64 方法 (DataView)](../../javascript/reference/getfloat64-method-dataview.md)|從開始檢視中取得指定的位元組位移的 Float64 值。|  
|[setInt8 方法 (DataView)](../../javascript/reference/setint8-method-dataview.md)|儲存在指定的位元組位移，從開始檢視的 Int8 值。|  
|[setUint8 方法 (DataView)](../../javascript/reference/setuint8-method-dataview.md)|儲存在指定的位元組位移，從開始檢視的 Uint8 值。|  
|[setInt16 方法 (DataView)](../../javascript/reference/setint16-method-dataview.md)|儲存在指定的位元組位移，從開始檢視的 Int16 值。|  
|[setUint16 方法 (DataView)](../../javascript/reference/setuint16-method-dataview.md)|儲存在指定的位元組位移，從開始檢視的 Uint16 值。|  
|[setInt32 方法 (DataView)](../../javascript/reference/setint32-method-dataview.md)|儲存在指定的位元組位移，從開始檢視的 Int32 值。|  
|[setUint32 方法 (DataView)](../../javascript/reference/setuint32-method-dataview.md)|儲存在指定的位元組位移，從開始檢視的 Uint32 值。|  
|[setFloat32 方法 (DataView)](../../javascript/reference/setfloat32-method-dataview.md)|儲存在指定的位元組位移，從開始檢視的 Float32 值。|  
|[setFloat64 方法 (DataView)](../../javascript/reference/setfloat64-method-dataview.md)|儲存在指定的位元組位移，從開始檢視的 Float64 值。|  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 DataView 物件來處理從 XmlHttpRequest 取得的二進位資料：  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]