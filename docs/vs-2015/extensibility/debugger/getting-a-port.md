---
title: 取得連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 809757df7d3a69eaf82bcda9fce78a45cece4e70
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183062"
---
# <a name="getting-a-port"></a>取得連接埠
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

連接埠代表處理程序執行所在機器的連線。 該電腦可能是本機電腦或遠端電腦 (這無法可能執行非 Windows 型作業系統，請參閱[連接埠](../../extensibility/debugger/ports.md)如需詳細資訊)。  
  
 連接埠由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面。 它用來取得的連接埠連接到電腦上執行的處理序的相關資訊。  
  
 偵錯引擎需要存取連接埠，以便與連接埠登錄程式節點，並滿足要求的處理程序資訊。 例如，如果偵錯引擎會實作[IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md)介面的實作[GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)方法可能需要的處理程序會要求連接埠要傳回的資訊。  
  
 Visual Studio 會提供必要的連接埠為偵錯引擎，它會從連接埠提供者中取得此連接埠。 如果程式已連結至 （內部偵錯工具，或因為發生例外狀況擲回，此觸發程序 Just in Time [JIT] 對話方塊中），則使用者可以選擇的傳輸 （如連接埠提供者的另一個名稱） 來使用。 否則為使用者啟動的偵錯工具中的程式時，如果專案系統會指定要使用的連接埠提供者。 Visual Studio 在可能情況下，具現化所代表的連接埠供應商[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面，並藉由呼叫要求新的連接埠[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)使用[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)介面。 此連接埠會接著傳遞給偵錯引擎中一份表單或另一個。  
  
## <a name="example"></a>範例  
 此程式碼片段示範如何使用提供的連接埠[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)註冊中的程式節點[ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)。 為了清楚起見已省略與這個概念沒有直接關聯的參數。  
  
> [!NOTE]
>  此範例會使用連接埠來啟動並繼續此程序，並假設[IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)連接埠上實作介面。 這不是唯一的方式來執行這些工作，您也可以，連接埠可能會不甚至會涉及以外的其他程式的[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)提供給它。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [正在登錄程式](../../extensibility/debugger/registering-the-program.md)   
 [啟用要偵錯程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [連接埠提供者](../../extensibility/debugger/port-suppliers.md)   
 [連接埠](../../extensibility/debugger/ports.md)

