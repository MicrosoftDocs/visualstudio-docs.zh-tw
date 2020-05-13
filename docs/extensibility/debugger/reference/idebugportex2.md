---
title: IDebugPortEx2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5789681b0da70f46dadac1e29d0d6bb9dc905d1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724994"
---
# <a name="idebugportex2"></a>IDebugPortEx2
此介面允許工作階段除錯管理員 (SDM) 控制在連接埠上執行的程式和進程。

## <a name="syntax"></a>語法

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 自定義埠供應商在實現[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)的同一對象上實現此介面。

## <a name="notes-for-callers"></a>通話備註
 SDM 在介面`IDebugPort2`上 調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugPortEx2`。

|方法|描述|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|啟動可執行檔。|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|恢復進程的執行。|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|確定是否可以終止進程。|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|終止進程。|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|獲取埠本身的進程 ID。|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|獲取與程式節點關聯的程式。|

## <a name="remarks"></a>備註
 此介面通常是 SDM 和自定義埠供應商之間的私有介面。

 如果需要,除錯引擎 (DE) 可以在[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面上尋找此介面,該介面傳遞給[Launch 暫停](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md),並使用[Launch 暫停](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)啟動程式。 但是,這不是要求,DE 可以執行啟動請求程式所需的任何操作。

## <a name="requirements"></a>需求
 標題: portpriv.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
