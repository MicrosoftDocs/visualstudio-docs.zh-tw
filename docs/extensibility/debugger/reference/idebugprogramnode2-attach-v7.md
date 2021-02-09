---
title: IDebugProgramNode2：： Attach_V7 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b143477dc558b20a302a54d5baecc64d02d33ea3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898637"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> 廢棄。 請勿使用。

## <a name="syntax"></a>語法

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>參數

`pMDMProgram`\
在 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面，表示要附加的程式。

`pCallback`\
在用來將 debug 事件傳送至 SDM 的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 介面。

`dwReason`\
在 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 列舉中的值，這個值會指定附加的原因。

## <a name="return-value"></a>傳回值

實作為應一律傳回 `E_NOTIMPL` 。

## <a name="remarks"></a>備註

> [!WARNING]
> 從 Visual Studio 2005，這個方法已不再使用，應該一律傳回 `E_NOTIMPL` 。 如果程式節點需要指出無法附加至或程式節點只是設定程式，請參閱 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 介面以取得替代方法 `GUID` 。 否則，請執行 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法。

## <a name="prior-to-visual-studio-2005"></a>在 Visual Studio 2005 之前

只有在要進行偵錯工具的位址空間中執行 DE 時，才需要執行這個方法。 否則，此方法應該會傳回 `S_FALSE` 。

當呼叫這個方法時，DE 必須傳送 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) 事件物件（如果它尚未針對這個 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 介面實例傳送），以及 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 和 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 事件物件。 如果參數為，則會傳送 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) 事件物件 `dwReason` `ATTACH_REASON_LAUNCH` 。

DE 必須在[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件物件所提供的[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件上呼叫[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法，並且必須將該程式的 GUID 儲存在 DE 所執行之物件的實例資料中 `IDebugProgram2` 。

## <a name="see-also"></a>另請參閱

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
