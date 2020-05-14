---
title: 取得連接埠 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738640"
---
# <a name="get-a-port"></a>取得連接埠
埠表示與運行進程的電腦的連接。 該電腦可以是本地電腦或遠端電腦(可能運行非基於 Windows 的作業系統;有關詳細資訊,請參閱[埠](../../extensibility/debugger/ports.md))。

埠由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面表示。 它用於獲取有關在埠連接到的電腦上運行的進程的資訊。

除錯引擎需要存取埠,以便向埠註冊程式節點並滿足行程資訊請求。 例如,如果調試引擎實現[IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md)介面,[則 GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)方法的實現可能會要求埠返回必要的進程資訊。

Visual Studio 向調試引擎提供必要的埠,並從埠供應商處獲取此埠。 如果程式附加到(從調試器內部或由於引發異常而觸發"即時 [JIT] 對話方塊"),則為使用者提供要使用的傳輸選擇(埠供應商的另一個名稱)。 否則,如果使用者從調試器中啟動程式,則專案系統指定要使用的埠供應商。 在這兩個事件中,Visual Studio 會實例化埠供應商(由[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面表示),並透過使用[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)介面調用[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)來請求新的埠。 然後,此埠以這種或另一種形式傳遞到調試引擎。

## <a name="example"></a>範例
此程式片段示範如何使用提供給[Launch 暫停](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)的埠在[ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)中註冊程式節點。 為了清楚起見,省略了與這一概念沒有直接關係參數的參數。

> [!NOTE]
> 本示例使用埠啟動和恢復該過程,並假定[IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)介面在埠上實現。 這絕不是執行這些任務的唯一方法,而且除了將程式的[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)交給它之外,埠可能甚至不涉及該埠。

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
- [開啟對程式進行除錯](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [港口供應商](../../extensibility/debugger/port-suppliers.md)
- [連接埠](../../extensibility/debugger/ports.md)
