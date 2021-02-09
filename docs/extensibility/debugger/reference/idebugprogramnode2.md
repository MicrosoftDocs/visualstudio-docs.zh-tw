---
title: IDebugProgramNode2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e6460653795720f10dca7f304035c49e4d8e035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898519"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
此介面代表可進行調試的程式。

## <a name="syntax"></a>Syntax

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 或自訂埠供應商會執行這個介面，以代表可進行調試的程式。 這個介面通常會在執行 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面的相同物件上執行。 這個介面是透過 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 呼叫 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)來註冊。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 以傳回這個介面。 自訂埠供應商會透過呼叫 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)來接收這個介面。 DE 會透過呼叫 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)來接收這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProgramNode2` 。

|方法|描述|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|取得程式的名稱。|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|取得裝載程式之進程的名稱。|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|取得裝載程式之進程的系統處理序識別碼。|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|廢棄。 請勿使用。|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|廢棄。 請勿使用。 如需替代方法，請參閱 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 介面。|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|取得執行此程式之 DE 的名稱和識別碼。|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|廢棄。 請勿使用。|

## <a name="remarks"></a>備註
 會話 debug manager (SDM) 通常會呼叫 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 來取得這個介面。

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
