---
title: 事件來源 (Visual Studio SDK) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], event sources
ms.assetid: b9ba0908-ae4c-4a64-aab1-bee453dd7a22
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0566468a7beaf7e50723c2e8e594e5cd2eebec79
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888604"
---
# <a name="event-sources-visual-studio-sdk"></a>事件來源 (Visual Studio SDK)
有兩個來源的事件： 偵錯引擎 (DE) 和工作階段進行偵錯管理員 (SDM)。 從裝置傳送的事件會有非 NULL 引擎，而從 SDM 傳送事件都有 NULL 引擎。  
  
## <a name="example"></a>範例  
 下列範例示範如何將傳送**IDebugProgramCreateEvent2**從以 SDM DE。  
  
```csharp  
CDebugProgramCreateEvent* pProgramCreateEvent = new CDebugProgramCreateEvent();  
if (FAILED(pCallback->Event(m_pEngine, NULL, m_pProgram, NULL, pProgramCreateEvent, IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS)))  
{  
   // Handle failure here.  
}  
]  
  
CEvent * pProgCreate = new CEvent(IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS);    
pProgCreate->SendEvent(pCallback, m_pEngine, (IDebugProgram2 *)this, NULL);  
  
HRESULT CEvent::SendEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {    
   HRESULT hr;    
  
   if (m_dwAttrib & EVENT_STOPPING)    
   {    
      hr = SendStoppingEvent(pCallback, pEngine, pProgram, pThread);    
   }    
   else if (m_dwAttrib & EVENT_SYNCHRONOUS)    
   {    
      hr = SendSynchronousEvent(pCallback, pEngine, pProgram, pThread);    
   }    
   else    
   {    
      assert(m_dwAttrib == 0);    
      hr = SendAsynchronousEvent(pCallback, pEngine, pProgram, pThread);    
   }    
  
   return hr;    
}    
  
HRESULT CEvent::SendAsynchronousEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {    
  
    HRESULT hr;    
  
   // Make sure the CEvent object running this code is not deleted until the code completes.    
   AddRef();    
  
   pCallback->Event(pEngine, NULL, pProgram, pThread, (IDebugEvent2 *)this, m_riid, m_dwAttrib);    
  
   // No error recovery here.    
   hr = S_OK;     
  
   Release();    
   return hr;    
}  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [傳送事件](../../extensibility/debugger/sending-events.md)