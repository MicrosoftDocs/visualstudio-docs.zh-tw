---
title: "IDebugPortEvents2::Event |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEvents2::Event
helpviewer_keywords: IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 82ea7d2c4a32bb224c8377a2980c944b3389da2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
這個方法會傳送表示的建立和解構的處理序和程式的連接埠上的事件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```csharp  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pMachine`  
 [in][IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)物件，表示偵錯伺服器 (每個執行個體的一個[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]) 中發生的事件。  
  
 `pPort`  
 [in][IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，表示發生事件的連接埠。  
  
 `pProcess`  
 [in][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，表示發生事件的程序。  
  
 `pProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示發生事件的程式。  
  
 `pEvent`  
 [in][IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)可識別事件的物件。 可能的事件如下：  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 [in]事件的 GUID。 因為事件轉換成[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)之前呼叫這個方法，這個識別碼可讓您更輕鬆地判斷正在傳送的事件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)