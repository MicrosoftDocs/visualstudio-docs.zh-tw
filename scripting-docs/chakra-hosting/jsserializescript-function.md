---
title: JsSerializeScript 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSerializeScript
helpviewer_keywords:
- JsSerializeScript function
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92bc6c1de0f2cd43dfe9566413fb64188fd5a382
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568868"
---
# <a name="jsserializescript-function"></a>JsSerializeScript 函式
將已剖析的指令碼序列化至緩衝區以重複使用。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `script`  
 要序列化的指令碼。  
  
 `buffer`  
 要放入序列化指令碼的緩衝區。 可以是 null。  
  
 `bufferSize`  
 容納序列化指令碼所需的緩衝區；亦即進入時，緩衝區的大小 (以位元組為單位)；結束時，緩衝區的大小 (以位元組為單位)。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 `JsSerializeScript` 會剖析指令碼，然後將指令碼的已剖析形式儲存為與執行階段無關的格式。 這麼一來，序列化的指令碼即可在任何執行階段還原序列化，而不需重新剖析指令碼。  
  
 需要使用中指令碼內容。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)