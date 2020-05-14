---
title: IDebug程序發佈者2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721533"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
此介面允許調試引擎 (DE) 或自定義埠供應商註冊程式進行調試。

## <a name="syntax"></a>語法

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
Visual Studio 實現此介面來註冊正在調試的程式,以便使其可見以跨多個進程進行調試。

## <a name="notes-for-callers"></a>通話備註
使用調用`CoCreateInstance``CLSID_ProgramPublisher`COM 的函數以獲取此介面(請參閱範例)。 DE 或自定義埠供應商使用此介面註冊表示正在調試的程式的程式節點。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|使程式節點可供 D 和工作階段調試管理員 (SDM)。|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|移除程式節點,使其不再可用。|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|使程式可供 D 和 SDM 使用。|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|移除程式,使其不再可用。|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|設置指示存在調試器的標誌。|

## <a name="remarks"></a>備註
此介面使程式和程式節點可用(即"發佈"它們),供D和工作階段調試管理員 (SDM) 使用。 要訪問已發佈的程式和程式節點,請使用[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面。 這是 Visual Studio 能夠識別正在調試程式的唯一方法。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="example"></a>範例
此示例演示如何實例化程式發行者和註冊程式節點。 這是從教學,[發佈程式節點](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae)。

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
