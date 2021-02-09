---
title: 取得埠 |Microsoft Docs
description: 瞭解 Visual Studio 如何提供埠給 debug engine，以向埠註冊程式節點，以及滿足處理常式資訊的要求。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f3ee9c145a4c6275f64d357d87ac1cc284bfac6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921293"
---
# <a name="get-a-port"></a>取得埠
埠代表與執行進程之電腦的連接。 該電腦可以是本機電腦或遠端電腦 (可能會執行非 Windows 作業系統;如需詳細資訊) ，請參閱 [埠](../../extensibility/debugger/ports.md) 。

埠是以 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 介面表示。 它是用來取得埠所連接之電腦上執行之進程的相關資訊。

偵錯工具引擎需要存取埠，才能向埠註冊程式節點，以及滿足處理常式資訊的要求。 例如，如果偵錯工具引擎會執行 [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) 介面，則 [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 方法的執行可能會要求傳回所需的進程資訊給埠。

Visual Studio 將必要的埠提供給 debug engine，並從埠供應商取得此埠。 如果程式是從偵錯工具內附加至 (，或因為擲回例外狀況而擲回例外狀況，而這會觸發) 的即時 [JIT] 對話方塊，則使用者會選擇傳輸 (另一個名稱供埠供應商) 使用。 否則，如果使用者從偵錯工具內啟動程式，則專案系統會指定要使用的埠供應商。 在任一事件中，Visual Studio 會將埠供應商（以[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面表示）具現化，並使用[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)介面呼叫[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)來要求新的埠。 然後，此埠會以一種形式傳遞至 debug engine。

## <a name="example"></a>範例
此程式碼片段說明如何使用提供給 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 的埠，在 [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)中註冊程式節點。 為了清楚起見，已省略與此概念不直接相關的參數。

> [!NOTE]
> 此範例會使用此埠來啟動並繼續處理常式，並假設 [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) 介面是在埠上執行。 這並不是唯一執行這些工作的方式，而且可能甚至不會涉及該埠，因為它會提供給它的程式 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 。

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
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>另請參閱
- [註冊程式](../../extensibility/debugger/registering-the-program.md)
- [啟用要進行調試的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [埠供應商](../../extensibility/debugger/port-suppliers.md)
- [連接埠](../../extensibility/debugger/ports.md)
