---
title: "JsGetArrayBufferStorage 函式 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 712ae298-36a9-47ef-b089-e51835c056bc
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a667325eb4d1d9540751a52232e5e06b3004b8b5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetarraybufferstorage-function"></a>JsGetArrayBufferStorage 函式
取得 `ArrayBuffer` 所使用的基礎記憶體儲存體。  
  
## <a name="syntax"></a>語法  
  
```  
JsErrorCode STDAPI_ JsGetArrayBufferStorage(  
   _In_ JsValueRef arrayBuffer,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### <a name="parameters"></a>參數  
 `arrayBuffer`  
 ArrayBuffer 執行個體。  
  
 `buffer`  
 ArrayBuffer 的緩衝區。 傳回的緩衝區存留期與 `ArrayBuffer` 的存留期相同。 用於記憶體回收的緩衝區指標不是 `ArrayBuffer` 的參考。  
  
 `bufferLength`  
 緩衝區中的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 需要使用中指令碼內容。  
  
 只有邊緣模式才支援這個 API。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)