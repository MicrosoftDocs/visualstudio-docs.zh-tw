---
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51f49ca90837cf80c22856ae2e8f89a98da43d86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869959"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
此介面代表可進行偵錯的程式。

## <a name="syntax"></a>語法

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 或自訂的連接埠提供者會實作這個介面來代表可進行偵錯的程式。 通常會實作這個介面上相同的物件會實作[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。 此介面已向[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]藉由呼叫[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)返回這個介面。 自訂連接埠供應商收到此介面，透過呼叫[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 DE 接收此介面，透過呼叫[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgramNode2`。

|方法|描述|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|取得程式的名稱。|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|取得裝載程式的處理序名稱。|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|取得裝載程式的處理序的系統處理序識別碼。|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|已被取代。 請勿使用。|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|已被取代。 請勿使用。 請參閱[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面，如需替代方法。|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|取得執行此程式 DE 識別碼與名稱。|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|已被取代。 請勿使用。|

## <a name="remarks"></a>備註
 工作階段的偵錯管理員 (SDM) 通常會呼叫[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)來取得這個介面。

## <a name="requirements"></a>需求
 標頭：Msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)