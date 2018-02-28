---
title: "JsRunSerializedScript 函式 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsRunSerializedScript
helpviewer_keywords:
- JsRunSerializedScript function
ms.assetid: 3fd3f6f1-eb3e-4751-92a5-c93b1035f3b2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b770edbcaa4e7dc36f295407627c10a8b574b88b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsrunserializedscript-function"></a>JsRunSerializedScript 函式
執行序列化的指令碼。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>參數  
 `script`  
 序列化指令碼的原始程式碼。  
  
 `buffer`  
 序列化的指令碼。  
  
 `sourceContext`  
 此 Cookie 會識別可偵錯指令碼內容所使用的指令碼。  
  
 `sourceUrl`  
 指令碼的來源位置。  
  
 `result`  
 執行指令碼的結果 (如果有的話)。 此參數可以是 null。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 需要使用中指令碼內容。  
  
 指令碼引擎未在記憶體中保存緩衝區，因此您的程式碼必須讓緩衝區保持運作中，而且一直持續到緩衝區可以用來執行指令碼為止。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)