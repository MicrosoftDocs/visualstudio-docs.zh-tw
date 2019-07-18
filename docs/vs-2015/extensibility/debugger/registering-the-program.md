---
title: 註冊計劃 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31d03f12a31953cbc0e20d06820dd49b5f9827e6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441977"
---
# <a name="registering-the-program"></a>註冊程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

偵錯引擎已取得的連接埠之後，由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面後，啟用要偵錯程式的下一個步驟是註冊的連接埠。 註冊之後，程式就會有可供偵錯由下列方式之一：  
  
- 程序的連結，可取得完整偵錯的控制權，執行中應用程式偵錯工具。  
  
- 在 just-in-time (JIT) 偵錯，以便之後事實偵錯的偵錯工具獨立執行的程式。 當執行階段架構會攔截錯誤時，偵錯工具會收到通知之前的作業系統，或執行階段環境釋放的記憶體和資源之錯誤的程式。  
  
## <a name="registering-procedure"></a>註冊程序  
  
#### <a name="to-register-your-program"></a>若要註冊您的程式  
  
1. 呼叫[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)藉由將連接埠的方法。  
  
     `IDebugPortNotify2::AddProgramNode` 需要指標[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面。  
  
     一般而言，當作業系統或執行階段環境載入程式，它會建立 [程式] 節點。 如果偵錯引擎 (DE) 會要求載入程式 DE 就會建立檔案，並註冊程式 節點中。  
  
     下列範例會顯示啟動程式，並註冊與連接埠的偵錯引擎。  
  
    > [!NOTE]
    > 這不是唯一的方式來啟動，並繼續處理序;這是主要的註冊計劃與連接埠的範例。  
  
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
                    hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)  
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
