---
title: JsCreateExternalArrayBuffer 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95459f9a9ff676f47d56ed584ad44a30f24fd4cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568028"
---
# <a name="jscreateexternalarraybuffer-function"></a>JsCreateExternalArrayBuffer 函式
建立 Javascript `ArrayBuffer` 物件來存取外部記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `data`  
 外部記憶體的指標。  
  
 `byteLength`  
 外部記憶體中的位元組數目。  
  
 `finalizeCallback`  
 物件完成時的回呼。 可能是 Null。  
  
 `callbackState`  
 將回傳給 finalizeCallback 的使用者提供狀態。  
  
 `result`  
 新的 `ArrayBuffer` 物件。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 需要使用中指令碼內容。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)