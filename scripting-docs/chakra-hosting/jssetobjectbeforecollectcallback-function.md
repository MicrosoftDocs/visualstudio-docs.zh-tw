---
title: JsSetObjectBeforeCollectCallback 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a472e63afd909ee7bcb74cb2fdd1ae98d6a2938
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568918"
---
# <a name="jssetobjectbeforecollectcallback-function"></a>JsSetObjectBeforeCollectCallback 函式
設定在物件的記憶體回收之前執行階段所呼叫的回呼函式。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ref`  
 要註冊回呼的物件。  
  
 `callbackState`  
 將回傳給回呼的使用者提供狀態。  
  
 `objectBeforeCollectCallback`  
 正在設定的回呼函式。 使用 Null 可清除先前註冊的回呼。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 會在目前執行階段的執行緒上叫用此回呼，因此直到完成回呼之前會封鎖執行。  
  
 只有邊緣模式才支援這個 API。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)