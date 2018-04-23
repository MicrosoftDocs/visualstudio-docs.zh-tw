---
title: IDebugProcess2::Attach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56f14b399a904c2584e81c2b6c8f344654b69a18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
將工作階段的偵錯管理員 (SDM) 附加至處理程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)來進行偵錯事件通知的物件。  
  
 `rgguidSpecificEngines`  
 [in]用來偵錯的處理序中執行程式的偵錯引擎的 Guid 陣列。 這個參數可以是 null 值。 如需詳細資訊，請參閱 < 備註 >。  
  
 `celtSpecificEngines`  
 [in]引擎中的偵錯數目`rgguidSpecificEngines`陣列和大小`rghrEngineAttach`陣列。  
  
 `rghrEngineAttach`  
 [in、 out]偵錯引擎所傳回的 HRESULT 代碼的陣列。 這個陣列的大小以指定`celtSpecificEngines`參數。 每個程式碼通常是 `S_OK`或`S_ATTACH_DEFERRED`。 後者表示 DE 目前已連結至任何程式。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 下表顯示其他可能的值。  
  
|值|描述|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的處理序已附加偵錯工具。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Attach 程序期間，發生安全性違規。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面的程序無法附加至偵錯工具。|  
  
## <a name="remarks"></a>備註  
 附加至處理序會將附加至可進行偵錯引擎 (DE) 中指定偵錯該處理序中執行的所有程式的 SDM`rgguidSpecificEngines`陣列。 設定`rgguidSpecificEngines`參數為 null 值或包含`GUID_NULL`陣列中要附加至處理序中的所有程式。  
  
 處理序中發生的所有偵錯事件傳送至給定[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件。 這`IDebugEventCallback2`SDM 呼叫這個方法時，提供物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)