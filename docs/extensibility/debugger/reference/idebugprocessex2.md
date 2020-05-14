---
title: IDebugProcessEx2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723336"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
此介面允許工作階段除錯管理員 (SDM) 通知它附加到的進程或從行程分離的進程。

## <a name="syntax"></a>語法

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 自訂埠供應商在[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面的同一物件上實現此介面,以便:

- 支援追蹤連線到行程的工作階段

- 支援跨多個除錯引擎自動附加

  如果選擇,自定義埠供應商可以實現此介面。

## <a name="notes-for-callers"></a>通話備註

- SDM`IDebugProcess2`在介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProcessEx2`。

|方法|描述|
|------------|-----------------|
|[附加](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|通知進程工作階段正在調試進程。|
|[中斷連結](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|通知進程會話不再調試進程。|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|為除錯引擎清單添加程式節點。|

## <a name="remarks"></a>備註
 此介面在 SDM 和進程之間是私有的。

## <a name="requirements"></a>需求
 標題: 波特普里夫.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
