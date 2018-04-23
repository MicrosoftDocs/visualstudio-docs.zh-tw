---
title: 註冊程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: febc798888cc046e514db4013edb077e25f5aaca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="registering-the-program"></a>註冊程式
偵錯引擎取得連接埠之後，由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面，啟用偵錯程式下一步是註冊該連接埠。 註冊之後，程式會用於偵錯由下列方式的其中一個：  
  
-   程序附加，可取得完整的偵錯控制權的執行中應用程式偵錯工具。  
  
-   在 just-in-time (JIT) 偵錯，以便允許獨立偵錯工具執行的程式進行偵錯之後事實。 當執行階段架構會攔截錯誤時，偵錯工具會通知之前的作業系統，或執行階段環境釋放的記憶體和資源的失敗的程式。  
  
## <a name="registering-procedure"></a>註冊程序  
  
#### <a name="to-register-your-program"></a>若要註冊您的程式  
  
1.  呼叫[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)連接埠所實作的方法。  
  
     `IDebugPortNotify2::AddProgramNode` 需要指標[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面。  
  
     一般而言，當作業系統或執行階段環境載入程式，它會建立程式節點。 如果偵錯引擎 (DE) 會要求載入程式 DE 建立並註冊程式節點。  
  
     下列範例會顯示啟動程式和註冊的通訊埠的偵錯引擎。  
  
    > [!NOTE]
    >  這不是唯一的方式來啟動並繼續處理程序;這是主要程式登錄連接埠的範例。  
  
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
 [取得連接埠](../../extensibility/debugger/getting-a-port.md)   
 [啟用要偵錯的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)