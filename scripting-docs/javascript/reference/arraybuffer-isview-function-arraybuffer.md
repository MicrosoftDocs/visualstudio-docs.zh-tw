---
title: ArrayBuffer.isView 函式 (ArrayBuffer) |Microsoft 文件
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
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5aaae2acb38aa2f8c4b5e49ea203e86665315700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633368"
---
# <a name="arraybufferisview-function-arraybuffer"></a>ArrayBuffer.isView 函式 (ArrayBuffer)
決定物件是否提供緩衝區的檢視。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
ArrayBuffer.isView(object)  
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 必要項。 要測試的物件。  
  
## <a name="return-value"></a>傳回值  
 如果下列任一值為 true 則為 `true`：  
  
-   `object` 是 `DataView` 物件。  
  
-   `object` 是類型陣列。  
  
 否則，方法會傳回 `false`。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例說明如何使用 `isView` 函式測試類型陣列和 `DataView` 物件。  
  
```JavaScript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Uint8ClampedArray 物件](../../javascript/reference/uint8clampedarray-object-javascript.md)