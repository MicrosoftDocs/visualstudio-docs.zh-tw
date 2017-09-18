---
title: "IDebugProgramNode2::Attach_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::Attach"
helpviewer_keywords: 
  - "IDebugProgramNode2::Attach_V7"
  - "IDebugProgramNode2::Attach"
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

被取代。  請勿使用。  
  
## 語法  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```c#  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### 參數  
 `pMDMProgram`  
 \[in\][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)代表附加至程式的介面。  
  
 `pCallback`  
 \[in\][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)是用來將偵錯事件傳送至 SDM 的介面。  
  
 `dwReason`  
 \[in\]介於[ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)指定的原因，讓您附加的列舉型別。  
  
## 傳回值  
 實作應該一律會傳回`E_NOTIMPL`。  
  
## 備註  
  
> [!WARNING]
>  起[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]，這個方法已不再使用，而且應該永遠會傳回`E_NOTIMPL`。  請參閱[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面的另一個方法，如果需要指出不能將它附加至 \[程式\] 節點，或 \[程式\] 節點就只需要設定程式`GUID`。否則，實作[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。  
  
## Visual Studio 2005年之前  
 這個方法只需要 DE 會在位址空間正在偵錯程式時，才需要實作。  否則，這個方法會傳回`S_FALSE`。  
  
 呼叫這個方法時，必須傳送 DE [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)事件物件，如果它沒有已傳送之執行個體的[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面，以及[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)和[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)事件的物件。  [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)事件物件，然後送出如果`dwReason`參數是`ATTACH_REASON_LAUNCH`。  
  
 必須呼叫 DE [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)上的方法[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件所提供的[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件物件，而且必須將該程式的 GUID 儲存在的執行個體資料`IDebugProgram2` DE 所實作的物件。  
  
## 請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)