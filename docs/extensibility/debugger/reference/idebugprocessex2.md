---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef8fd848ed1a8298cc4ea8a5ce9d2c0463a2b779
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693595"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
此介面可讓偵錯管理員 (SDM) 通知的程序，它會附加至或從處理序中斷連結的工作階段。

## <a name="syntax"></a>語法

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 自訂連接埠供應商的相同物件上實作這個介面[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面才能：

- 支援追蹤的工作階段連線到處理程序

- 支援自動附加跨多個偵錯引擎

  自訂連接埠供應商可以實作這個介面，如果選擇。

## <a name="notes-for-callers"></a>呼叫端資訊

-   SDM 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugProcess2`介面，以取得此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProcessEx2`。

|方法|描述|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|通知程序工作階段現在正在偵錯程序。|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|通知程序工作階段不會再偵錯程序。|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|加入程式節點，如需偵錯引擎的清單。|

## <a name="remarks"></a>備註
 這個介面是 SDM 和處理序之間的私用。

## <a name="requirements"></a>需求
 標頭：Portpriv.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)