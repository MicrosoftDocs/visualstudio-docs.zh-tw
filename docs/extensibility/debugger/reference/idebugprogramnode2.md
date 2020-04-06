---
title: IDebugProgramNode2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e6eac7c97b9d375f32e36a372d6f31175c79098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721922"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
此介面表示可以調試的程式。

## <a name="syntax"></a>語法

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 或自訂埠供應商實現此介面以表示可以調試的程式。 此介面通常實現於實現[IDebug Program2](../../../extensibility/debugger/reference/idebugprogram2.md)介面的同一物件上。 此介面通過調用[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)][PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)註冊。

## <a name="notes-for-callers"></a>通話備註
 調用[獲取提供程式程序節點](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)以返回此介面。 自定義埠供應商通過調用[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)接收此介面。 DE 通過調用[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)接收此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgramNode2`。

|方法|描述|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|獲取程式的名稱。|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|獲取承載程序的進程的名稱。|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|獲取承載程序的進程的系統進程標識符。|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|廢棄。 請勿使用。|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|廢棄。 請勿使用。 有關替代方法,請參閱[IDebugProgramNode Attach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面。|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|取得執行此程式的 DE 的名稱和識別碼。|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|廢棄。 請勿使用。|

## <a name="remarks"></a>備註
 工作階段除錯管理員 (SDM) 通常呼叫[GetProviderProgramnode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)以取得此介面。

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
