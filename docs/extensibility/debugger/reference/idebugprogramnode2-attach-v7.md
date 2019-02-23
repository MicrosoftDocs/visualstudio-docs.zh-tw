---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02022a4276da39fb863ccfed8ed02aa9d20f9c5c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689963"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> 已被取代。 請勿使用。

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

#### <a name="parameters"></a>參數

`pMDMProgram`

 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)代表要附加至程式的介面。

 `pCallback`

 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)介面，以用來將偵錯事件傳送到 SDM。

 `dwReason`

 [in]值，以從[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)列舉，指定將附加的原因。

## <a name="return-value"></a>傳回值

實作應該一律傳回`E_NOTIMPL`。

## <a name="remarks"></a>備註

> [!WARNING]
> 截至 Visual Studio 2005 中，這個方法不會再使用，並應該一律傳回`E_NOTIMPL`。 請參閱[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面的替代方法，如果需要指出無法將它附加至 [程式] 節點，或 [程式] 節點只需要設定程式`GUID`。 否則，實作[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。

## <a name="prior-to-visual-studio-2005"></a>Visual Studio 2005 之前

這個方法需要 DE 執行正在偵錯之程式的位址空間中時，才實作。 否則，此方法應傳回`S_FALSE`。

呼叫這個方法時，必須傳送 DE [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)事件物件，如果它沒有已傳送的這個執行個體[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面，以及[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)並[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)事件物件。 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)事件物件，便會如果`dwReason`參數是`ATTACH_REASON_LAUNCH`。

必須先呼叫 DE [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)提供的物件[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件物件，並必須儲存該程式的 GUID中的執行個體資料`IDebugProgram2`DE 所實作的物件。

## <a name="see-also"></a>另請參閱

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)