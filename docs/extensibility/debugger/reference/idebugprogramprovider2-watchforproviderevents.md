---
title: "IDebugProgramProvider2::WatchForProviderEvents | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::WatchForProviderEvents"
helpviewer_keywords: 
  - "IDebugProgramProvider2::WatchForProviderEvents"
ms.assetid: 2eb93653-b5fb-45b6-b136-56008c5d25ef
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgramProvider2::WatchForProviderEvents
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

允許的連接埠的事件通知程序。  
  
## 語法  
  
```cpp  
HRESULT WatchForProviderEvents(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   CONST_GUID_ARRAY     EngineFilter,  
   REFGUID              guidLaunchingEngine,  
   IDebugPortNotify2*   pEventCallback  
);  
```  
  
```c#  
int WatchForProviderEvents(  
   enum_PROVIDER_FLAGS   Flags,  
   IDebugDefaultPort2    pPort,  
   AD_PROCESS_ID         ProcessId,  
   CONST_GUID_ARRAY      EngineFilter,  
   ref Guid              guidLaunchingEngine,  
   IDebugPortNotify2     pEventCallback  
);  
```  
  
#### 參數  
 `Flags`  
 \[in\]從的旗標組合[PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)列舉型別。  下列旗標為這個呼叫一般項目：  
  
|旗標|描述|  
|--------|--------|  
|`PFLAG_REMOTE_PORT`|呼叫者正在遠端機器上執行。|  
|`PFLAG_DEBUGGEE`|呼叫端是否目前正在偵錯 \(每個節點會傳回封送處理的其他資訊\)。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|已附加至呼叫端，但不是啟動偵錯工具。|  
|`PFLAG_REASON_WATCH`|呼叫端想要監看的事件。  如果不設定這個旗標。  然後移除回呼事件並呼叫者不會再收到通知。|  
  
 `pPort`  
 \[in\]呼叫的處理程序的連接埠上執行。  
  
 `processId`  
 \[in\][AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構保留包含該程式的處理序 ID 有問題。  
  
 `EngineFilter`  
 \[in\]陣列的偵錯引擎處理程序相關聯的 Guid。  
  
 `guidLaunchingEngine`  
 \[in\]啟動這個處理程序 \(如果有的話\)，偵錯引擎的 GUID。  
  
 `pEventCallback`  
 \[in\][IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)會接收事件告知的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當呼叫端想要移除先前的呼叫這個方法來建立事件處理常式時，在呼叫端傳遞相同的參數如同第一次，但分葉關閉`PFLAG_REASON_WATCH`旗標。  
  
## 範例  
 下列範例會示範如何實作這個方法，如 **CDebugEngine** 物件，公開 \(expose\) [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面。  
  
```cpp#  
STDMETHODIMP CDebugEngine::WatchForProviderEvents(  
    PROVIDER_FLAGS Flags,   
    IDebugDefaultPort2 *pPort,   
    AD_PROCESS_ID processId,   
    CONST_GUID_ARRAY EngineFilter,   
    REFGUID guidLaunchingEngine,   
    IDebugPortNotify2 *pPortNotify)  
{  
    HRESULT hRes = E_FAIL;  
  
    if (EVAL(pPort != NULL) && EVAL(pPortNotify != NULL))  
    {  
        // We will only watch/send events about the process if the debugger  
        // is actually debugging the process, and only if this is an attach or a LoRIE launch  
        if (IsFlagSet(Flags, PFLAG_DEBUGGEE) &&  
            guidLaunchingEngine == GUID_NULL &&  
            processId.ProcessIdType == AD_PROCESS_ID_SYSTEM)  
        {  
            // We don't support WatchForProviderEvents when in interop mode  
            if (m_fInterop)  
            {  
                ASSERT(!"Shouldn't ever be called in interop mode");  
                hRes = E_FAIL;  
            }  
            else  
            {  
                if (IsFlagSet(Flags, PFLAG_REASON_WATCH))  
                {  
                    // QI to get IDebugEventCallback2 which is required.  
                    CComQIPtr<IDebugEventCallback2> pCallback(pPortNotify);  
  
                    ASSERT(pCallback != NULL);  
                    if ( pCallback != NULL )  
                    {  
                        // Register the callback  
                        hRes = this->InitDebugSession(pCallback);  
  
                        if ( S_OK == hRes )  
                        {  
                            // Get the IDebugProcess2 from the port and call AttachImpl  
                            CComPtr<IDebugProcess2> spProcess;  
  
                            hRes = pPort->GetProcess(processId, &spProcess);  
  
                            if (HREVAL(S_OK, hRes))  
                            {  
                                hRes = AttachImpl(spProcess, NULL, NULL, processId.ProcessId.dwProcessId, ATTACH_REASON_USER, NULL);  
  
                                if ( FAILED(hRes) && (!m_pPidList || 0 == m_pPidList->GetCount()) )  
                                    this->Cleanup();  
                            }  
                        }  
                        else  
                            this->Cleanup();  
                    }  
                    else  
                        hRes = E_FAIL;  
                }  
                else  
                {  
                    // Detach will be done by SDM calling on programs directly if there are managed programs.  
  
                    // This handling is the case where no managed code ever ran.  
                    if ( this->IsProcessBeingDebugged(processId.ProcessId.dwProcessId) )  
                    {  
                        ProgramList *pProgList = this->GetProgramListCopy();  
  
                        if ( EVAL(pProgList) )  
                        {  
                            if ( pProgList->GetCount() == 0)  
                            {  
                                CComPtr<ICorDebugProcess> pCorProcess;  
  
                                hRes = this->GetCorProcess(processId.ProcessId.dwProcessId, &pCorProcess);  
  
                                if (HREVAL(S_OK, hRes) )  
                                {  
                                    hRes = pCorProcess->Stop(INFINITE);  
  
                                    if ( HREVAL(S_OK, hRes) )  
                                        hRes = pCorProcess->Detach();  
                                }  
  
                                // Tell the engine that it should unregister this process from com+  
                                this->UnregisterProcess(processId.ProcessId.dwProcessId);  
  
                                // If there are no more pids left then cleanup everything.  
                                if ( 0 == m_pPidList->GetCount() )  
                                    this->Cleanup();  
                            }  
                            // This is needed for cases where the SDM has not yet recieved program create  
                            // by the time that we need to detach (example: the managed attach succeeds,  
                            // but some other attach step fails).  
                            else  
                            {  
                                PROGNODE *pProgNode = NULL;  
                                while ( pProgNode = pProgList->Next(pProgNode) )  
                                {  
                                    CDebugProgram * pProgram = ((CDebugProgram *)pProgNode->data);  
                                    hRes = pProgram->Detach();  
                                }  
                            }  
  
                            delete pProgList;  
                        }  
                    }  
                    else  
                        hRes = S_OK;  
                }  
            }  
        }  
        else  
        {  
            hRes = S_FALSE;  
        }  
    }  
    else  
    {  
        hRes = E_INVALIDARG;  
    }  
  
    return hRes;  
}  
```  
  
## 請參閱  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)