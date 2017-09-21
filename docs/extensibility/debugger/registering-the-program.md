---
title: "註冊程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "註冊的程式"
  - "偵錯 [偵錯 SDK]，程式註冊"
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 註冊程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯引擎取得連接埠之後，由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面，啟用偵錯程式，下一步是用連接埠來登錄它。  一旦登錄，就有一個程式適用於偵錯的下列方法之一：  
  
-   程序附加，它可讓偵錯工具執行的應用程式完全偵錯的控制。  
  
-   只要精準 \(JIT\) 偵錯時，它可讓之後事實偵錯的獨立於偵錯工具執行的程式。  當執行階段架構會攔截錯誤時，偵錯工具會被通知之前的作業系統，或執行階段環境釋放的記憶體和資源之錯誤的程式。  
  
## 註冊程序  
  
#### 若要註冊您的程式  
  
1.  呼叫[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)連接埠所實作的方法。  
  
     `IDebugPortNotify2::AddProgramNode`需要有指向指標[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面。  
  
     一般而言，當作業系統或執行階段環境載入程式時，它就會建立 \[程式\] 節點。  如果偵錯引擎 \(DE\) 會詢問您是否可以載入程式 DE 就會建立檔案，並登錄程式\] 節點中。  
  
     下列範例會示範偵錯引擎啟動的程式，以及註冊與連接埠。  
  
    > [!NOTE]
    >  這不是唯一的方式來啟動，並繼續處理程序。 這是主要的範例登錄程式與連接埠。  
  
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
 [取得連接埠](../../extensibility/debugger/getting-a-port.md)   
 [啟用偵錯程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)