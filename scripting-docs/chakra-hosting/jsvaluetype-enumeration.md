---
title: JsValueType 列舉 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsValueType
helpviewer_keywords:
- JsValueType enumeration
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4f61cf9118c19a0fc35e7505af422b812d0b43
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569048"
---
# <a name="jsvaluetype-enumeration"></a>JsValueType 列舉
JsValueRef 的 JavaScript 類型。  
  
## <a name="syntax"></a>語法  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## <a name="members"></a>Members  
  
### <a name="values"></a>值  
  
|名稱|說明|  
|----------|-----------------|  
|`JsUndefined`|該值是 `undefined` 值。|  
|`JsNull`|該值是 `null` 值。|  
|`JsNumber`|此值為 JavaScript 數字值。|  
|`JsString`|此值為 JavaScript 字串值。|  
|`JsBoolean`|此值為 JavaScript 布林值。|  
|`JsObject`|此值為 JavaScript 物件值。|  
|`JsFunction`|此值為 JavaScript 函式物件值。|  
|`JsError`|此值為 JavaScript 錯誤物件值。|  
|`JsArray`|此值為 JavaScript 陣列物件值。|  
|`JsSymbol`|此值為 JavaScript 符號值。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsArrayBuffer`|此值為 JavaScript `ArrayBuffer` 物件值。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsTypedArray`|此值為 JavaScript 類型的陣列物件值。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsDataView`|此值為 JavaScript `DataView` 物件值。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)