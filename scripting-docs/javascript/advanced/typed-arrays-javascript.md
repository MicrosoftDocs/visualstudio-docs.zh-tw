---
title: "具類型陣列 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5fc3b29a4593e7c627a6e606242229e87fa5be54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="typed-arrays-javascript"></a>類型陣列 (JavaScript)
您可以使用類型陣列來處理二進位資料，資料來自例如網路通訊協定、二進位檔案格式，以及原始圖形緩衝區等來源。 類型陣列也可用來管理記憶體中具有已知位元組版面配置的二進位資料。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)以回應 [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx)。 您可以使用 [DataView 物件](../../javascript/reference/dataview-object.md)的不同方法，或是將位元組複製到適當的具類型陣列，來操作回應中的位元組。  
  
> [!TIP]
>  如需搭配使用不同回應類型與 `XmlHttpRequest` 的詳細資訊，請參閱 [XMLHttpRequest.responseType](http://msdn.microsoft.com/en-us/8d7738d1-4bfd-4cf1-8015-174def089556)、[XMLHttpRequest 增強功能](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069)和[下載不同類型的內容 (Windows 市集應用程式)](http://msdn.microsoft.com/en-us/c0006bbd-17f9-4c6a-af81-2acaf109111d)。  
  
```JavaScript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## <a name="arraybuffer"></a>ArrayBuffer  
 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)代表原始資料的緩衝區，用來儲存不同具類型陣列的資料。 您無法讀取或寫入 `ArrayBuffer`，但可以將它傳遞給具類型陣列或 [DataView 物件](../../javascript/reference/dataview-object.md)以解譯原始緩衝區。 您可以使用 `ArrayBuffer` 來儲存任何種類的資料 (或混合的資料類型)。  
  
## <a name="dataview"></a>DataView  
 您可以使用 [DataView 物件](../../javascript/reference/dataview-object.md)來讀取和寫入不同類型的二進位資料至 `ArrayBuffer` 中的任何位置。  
  
## <a name="typed-arrays"></a>具類型陣列  
 具類型陣列的類型代表 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)的檢視，可以編製索引及操作。 所有的陣列類型都是固定長度。  
  
||||  
|-|-|-|  
|名稱|大小 (以位元組為單位)|說明|  
|[Int8Array 物件](../../javascript/reference/int8array-object.md)|1|8 位元二補數帶正負號的整數|  
|[Uint8Array 物件](../../javascript/reference/uint8array-object.md)|1|16 位元不帶正負號的整數|  
|[Int16Array 物件](../../javascript/reference/int16array-object.md)|2|16 位元二補數帶正負號的整數|  
|[Uint16Array 物件](../../javascript/reference/uint16array-object.md)|2|16 位元不帶正負號的整數|  
|[Int32Array 物件](../../javascript/reference/int32array-object.md)|4|32 位元二補數帶正負號的整數|  
|[Uint32Array 物件](../../javascript/reference/uint32array-object.md)|4|32 位元不帶正負號的整數|  
|[Float32Array 物件](../../javascript/reference/float32array-object.md)|4|32 位元 IEEE 浮點數|  
|[Float64Array 物件](../../javascript/reference/float64array-object.md)|8|64 位元 IEEE 浮點數|