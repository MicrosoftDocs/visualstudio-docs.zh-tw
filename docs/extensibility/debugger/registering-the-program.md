---
title: 註冊程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b68fa67f784d155288482ad724b632ed5ba5fa41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713163"
---
# <a name="register-the-program"></a>註冊程式
調試引擎獲取了由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面表示的埠後,使程序進行調試的下一步是將其註冊到埠。 註冊后,程式可通過以下方式之一進行調試:

- 附加過程,它允許調試器獲得正在運行的應用程式的完整調試控制。

- 即時 (JIT) 除錯,允許對獨立於除錯器運行的程式進行事後調試。 當運行時體系結構捕獲故障時,在操作系統或運行時環境釋放故障程式的記憶體和資源之前通知調試器。

## <a name="registering-procedure"></a>註冊過程

### <a name="to-register-your-program"></a>註冊您的程式

1. 調用埠實現的[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)方法。

     `IDebugPortNotify2::AddProgramNode`需要指向[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面的指標。

     通常,當作業系統或運行時環境載入程式時,它會創建程式節點。 如果要求調試引擎 (DE) 載入程式,DE 將建立並註冊程式節點。

     下面的範例顯示調試引擎啟動程式並將其註冊到埠。

    > [!NOTE]
    > 此代碼示例不是啟動和恢復進程的唯一方法;因此,此過程不是啟動和恢復進程的唯一方法。此代碼主要是將程式註冊到埠的範例。

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
- [取得連接埠](../../extensibility/debugger/getting-a-port.md)
- [開啟對程式進行除錯](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
