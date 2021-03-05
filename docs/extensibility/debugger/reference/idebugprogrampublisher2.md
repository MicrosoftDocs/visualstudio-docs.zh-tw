---
description: 此介面可讓 debug engine (DE) 或自訂埠供應商來註冊程式以進行偵錯工具。
title: IDebugProgramPublisher2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: deac68ba693bd9e4f827fef5610e3c9d2c3c26f6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166966"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
此介面可讓 debug engine (DE) 或自訂埠供應商來註冊程式以進行偵錯工具。

## <a name="syntax"></a>Syntax

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
Visual Studio 會執行這個介面以註冊要進行偵錯工具的程式，以便在多個進程之間進行跨進程的偵錯工具。

## <a name="notes-for-callers"></a>呼叫者注意事項
使用呼叫 COM 的函式 `CoCreateInstance` `CLSID_ProgramPublisher` 來取得此介面 (請參閱範例) 。 DE 或自訂埠供應商會使用此介面來註冊程式節點，以代表要進行偵錯工具的程式。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|使程式節點可供 DEs 和會話 debug manager (SDM) 。|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|移除程式節點，使其無法再使用。|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|使程式可供 DEs 和 SDM 使用。|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|移除程式，使其無法再使用。|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|設定旗標，指出偵錯工具存在。|

## <a name="remarks"></a>備註
此介面讓程式和程式節點可供使用， (也就是「發佈」它們) 供 DEs 和會話 debug manager (SDM) 使用。 若要存取已發佈的程式和程式節點，請使用 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) 介面。 這是 Visual Studio 可辨識程式正在進行調試的唯一方式。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>範例
此範例示範如何將程式發行者具現化，並註冊程式節點。 這是取自教學 [課程的發行程式節點](/previous-versions/bb161795(v=vs.90))。

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
