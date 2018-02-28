---
title: "JsStartDebugging 函式 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsStartDebugging
helpviewer_keywords:
- JsStartDebugging function
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9b7e3deb407d1a1e9d16db38e17c85ccc8c797
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsstartdebugging-function"></a>JsStartDebugging 函式
在目前的內容中開始程式碼剖析。  
  
## <a name="syntax"></a>語法  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### <a name="parameters"></a>參數  
 `debugApplication`  
 用於偵錯的偵錯應用程式。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 主應用程式應該要確定已使用 `COINIT_MULTITHREADED` 或 `COINIT_APARTMENTTHREADED` 呼叫 `CoInitializeEx` 至少一次，才能使用此 API。  
  
 邊緣模式不支援 `debugApplication` 參數。 如需以邊緣模式使用此 API 的詳細資訊，請參閱[以 Edge 和舊版引擎為目標](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)