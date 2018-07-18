---
title: IDebugEventCallback2::Event |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ea52b8be040df50da1585165599c4fdea635557
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117653"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
傳送通知的偵錯事件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pEngine`  
 [in][IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)物件，表示偵錯引擎 (DE) 傳送此事件。 DE 需要填寫此參數。  
  
 `pProcess`  
 [in][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，表示發生事件時的程序。 這個參數會填入的工作階段的偵錯管理員 (SDM)。 DE 一律會傳遞這個參數的 null 值。  
  
 `pProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示的程式發生此事件。 對於大部分的事件，此參數不是 null 值。  
  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示發生此事件的執行緒。 停止事件，此參數不能為 null 值，與堆疊框架取自此參數。  
  
 `pEvent`  
 [in][IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)物件，表示偵錯事件。  
  
 `riidEvent`  
 [in]GUID，識別哪些事件介面，以取得從`pEvent`參數。  
  
 `dwAttrib`  
 [in]從旗標的組合[EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)列舉型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當呼叫這個方法，`dwAttrib`參數必須符合的傳回值[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)事件物件上呼叫的方法傳入`pEvent`參數。  
  
 所有偵錯事件以非同步的方式，不論事件本身是否為非同步回傳。 當 DE 呼叫這個方法時，傳回的值不會指出是否已處理的事件，僅是否接收到事件。 事實上，在大部分情況下，事件尚未處理此方法傳回時。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)