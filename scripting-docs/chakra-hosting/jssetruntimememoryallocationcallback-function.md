---
title: "JsSetRuntimeMemoryAllocationCallback 函式 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryAllocationCallback
helpviewer_keywords:
- JsSetRuntimeMemoryAllocationCallback function
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 755ab36c8edb8c0350eb2b245e060344c8825dee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememoryallocationcallback-function"></a>JsSetRuntimeMemoryAllocationCallback 函式
為指定的執行階段設定記憶體配置回呼  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### <a name="parameters"></a>參數  
 `runtime`  
 要為其註冊配置回呼的執行階段。  
  
 `callbackState`  
 將回傳給回呼的使用者提供狀態。  
  
 `allocationCallback`  
 要為記憶體配置事件被呼叫的記憶體配置回呼。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 註冊記憶體配置回呼將使該執行階段在從作業系統取得記憶體時，或在釋放記憶體至作業系統時對主機回呼。 在該執行階段記憶體管理員配置記憶體區塊前呼叫此回呼常式。 如果回呼傳回 false，就會拒絕此配置。 執行階段記憶體管理員也會在釋放記憶體區塊之後叫用回呼常式，而在配置失敗之後亦同。  
  
 會在目前執行階段的執行緒上叫用此回呼，因此直到完成回呼之前會封鎖執行。  
  
 不會儲存此回呼的傳回值；先前已拒絕的配置不會防止執行階段之後再為了新的記憶體配置而叫用回呼。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)