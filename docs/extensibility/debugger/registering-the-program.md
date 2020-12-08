---
title: 註冊程式 |Microsoft Docs
description: 瞭解 debug 引擎取得埠之後，要如何使用埠註冊程式。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 80c3d13cc7319e43390a7e9e6f4eb42a5a87c780
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847092"
---
# <a name="register-the-program"></a>註冊程式
在偵測引擎取得埠（以 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 介面表示）之後，啟用要進行偵錯工具的下一個步驟是向埠註冊程式。 註冊之後，程式便可透過下列其中一種方式進行偵錯工具：

- 附加的處理常式，可讓偵錯工具對執行中的應用程式進行完整的偵錯工具控制。

- 即時 (JIT) 的偵錯工具，可讓您在偵錯工具以外執行的程式進行事後的偵錯工具。 當執行時間架構攔截到錯誤時，偵錯工具會在作業系統或執行時間環境釋放失敗程式的記憶體和資源之前收到通知。

## <a name="registering-procedure"></a>正在註冊程式

### <a name="to-register-your-program"></a>註冊您的程式

1. 呼叫由埠所執行的 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 方法。

     `IDebugPortNotify2::AddProgramNode` 需要 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 介面的指標。

     通常，當作業系統或執行時間環境載入程式時，它會建立程式節點。 如果 debug engine (DE) 被要求載入程式，則取消會建立並註冊程式節點。

     下列範例顯示啟動程式並使用埠註冊程式的 debug engine。

    > [!NOTE]
    > 這個程式碼範例不是啟動和繼續處理常式的唯一方法;這段程式碼主要是使用埠註冊程式的範例。

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
- [取得埠](../../extensibility/debugger/getting-a-port.md)
- [啟用要進行調試的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
