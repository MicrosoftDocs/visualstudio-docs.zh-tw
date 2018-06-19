---
title: 取得連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c20b3e3bdc2644e7af7d9a35de06af7f96d7680
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102989"
---
# <a name="getting-a-port"></a>取得連接埠
連接埠代表處理程序執行所在電腦的連接。 該電腦可能會在本機電腦或遠端電腦 (其中可能可能執行非 windows 作業系統，請參閱 <<c0> [ 連接埠](../../extensibility/debugger/ports.md)如需詳細資訊)。  
  
 連接埠由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面。 它用來取得連接埠連接到電腦上執行的處理序的相關資訊。  
  
 偵錯引擎需要存取連接埠，以便與連接埠登錄程式節點，並滿足要求的處理程序資訊。 例如，如果偵錯引擎實作[IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md)介面的實作[GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)方法可能需要的處理程序會要求連接埠要傳回的資訊。  
  
 Visual Studio 會提供必要的通訊埠，以偵錯引擎，它會從連接埠供應商取得此連接埠。 如果程式附加至 （或從偵錯工具內因為發生例外狀況已擲回，此觸發程序中即時恰好 [JIT] 對話方塊中），使用者可以使用所選擇的傳輸 （通訊埠供應商的另一個名稱）。 否則，如果使用者啟動的偵錯工具內的程式，專案系統會指定要使用的連接埠供應商。 Visual Studio 在可能情況下，具現化所代表的連接埠供應商[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面，並藉由呼叫要求新的連接埠[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)與[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)介面。 此連接埠接著傳遞至偵錯引擎，在表單或另一個。  
  
## <a name="example"></a>範例  
 此程式碼片段示範如何使用提供給連接埠[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)登錄中的程式節點[ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)。 為了清楚起見省略了這個概念不直接相關聯的參數。  
  
> [!NOTE]
>  此範例中使用的連接埠，以啟動並繼續執行程序，並假設[IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)連接埠上實作介面。 這是不是唯一的方式來執行這些工作，而且很可能的連接埠可能不甚至會影響到以外該程式[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)提供給它。  
  
```cpp  
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
  
## <a name="see-also"></a>另請參閱  
 [註冊程式](../../extensibility/debugger/registering-the-program.md)   
 [啟用要進行偵錯的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [連接埠供應商](../../extensibility/debugger/port-suppliers.md)   
 [連接埠](../../extensibility/debugger/ports.md)