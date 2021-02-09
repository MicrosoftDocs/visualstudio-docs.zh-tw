---
title: IDebugProcessEx2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e8966be5c30bf2061fc1e03be6798279afbe8ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900169"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
此介面可讓會話 debug manager (SDM) 通知正在附加或卸離進程的進程。

## <a name="syntax"></a>Syntax

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 自訂通訊埠供應商會在與 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 介面相同的物件上執行這個介面，以便：

- 支援追蹤連接到進程的會話

- 支援跨多個 debug 引擎的自動附加

  自訂埠供應商可以在選擇的情況下，執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項

- SDM 會呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugProcess2` 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProcessEx2` 。

|方法|描述|
|------------|-----------------|
|[附加](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|通知進程，會話現在正在將進程進行偵錯工具。|
|[卸離](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|通知進程，會話不再將進程進行偵錯工具。|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|加入程式節點以取得 debug 引擎的清單。|

## <a name="remarks"></a>備註
 這個介面在 SDM 和進程之間是私用的。

## <a name="requirements"></a>規格需求
 標頭： Portpriv。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
