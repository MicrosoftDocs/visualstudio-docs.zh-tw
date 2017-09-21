---
title: "取得連接埠 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "連接埠，以取得"
  - "偵錯 [偵錯 SDK]，連接埠"
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 取得連接埠
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

連接埠表示處理程序執行所在電腦的連接。  該電腦可能是本機電腦或遠端電腦 \(這可能無法執行非 windows 作業系統。 請參閱[連接埠](../../extensibility/debugger/ports.md)如需詳細資訊\)。  
  
 連接埠由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面。  它用來取得連接埠連接到電腦上執行的處理序的資訊。  
  
 偵錯引擎會需要存取連接埠，才能註冊程式節點與連接埠，並滿足要求的處理程序資訊。  例如，如果偵錯引擎實作[IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md)介面，用於實作[GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)方法可能會要求要傳回所需的處理序資訊的連接埠。  
  
 Visual Studio 提供必要的連接埠偵錯引擎，而且它會從連接埠提供者中取得此連接埠。  如果程式附加到 \(可能是來自於偵錯工具，或因例外狀況擲，而觸發的正精準 \[JIT\] 對話方塊中，該資料\)，提供使用者選擇的傳輸 \(如連接埠提供者的另一個名稱\) 使用。  否則，如果使用者啟動程式使其無法於偵錯工具時，專案系統會指定要使用的連接埠提供者。  在可能情況下，Visual Studio 的執行個體化連接埠提供者，以表示[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面，並索取新的連接埠，藉由呼叫[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)與[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)介面。  這個連接埠然後傳遞給偵錯引擎在一個表單中的或另一個。  
  
## 範例  
 這個程式碼片段顯示如何使用提供的連接埠[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)登錄程式\] 節點，在[ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)。  為了清楚起見省略了這個概念不是直接相關的參數。  
  
> [!NOTE]
>  本範例使用的通訊埠來啟動，並繼續處理程序，並假設[IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)連接埠上實作介面。  這是不可能是唯一能執行這些工作，而且可以連接埠可能不甚至會涉及以外的其他程式的[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)提供給它。  
  
```cpp#  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## 請參閱  
 [註冊程式](../../extensibility/debugger/registering-the-program.md)   
 [啟用偵錯程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [連接埠供應商](../../extensibility/debugger/port-suppliers.md)   
 [連接埠](../../extensibility/debugger/ports.md)