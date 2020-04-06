---
title: IDebugProgramNode2::Attach_V7 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722135"
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
[在][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面,表示要附加到的程式。

`pCallback`\
[在]用於將除錯事件發送到 SDM 的[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)介面。

`dwReason`\
[在]ATTACH_REASON[枚舉中](../../../extensibility/debugger/reference/attach-reason.md)指定附加原因的值。

## <a name="return-value"></a>傳回值

實現應始終返回`E_NOTIMPL`。

## <a name="remarks"></a>備註

> [!WARNING]
> 自 Visual Studio 2005 起,此方法不再使用`E_NOTIMPL`,應始終返回 。 如果程式節點需要指示它不能附加到,或者程式節點只是設置程式`GUID`,請參閱[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面,瞭解替代方法。 否則,實現[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。

## <a name="prior-to-visual-studio-2005"></a>2005年之前的視覺工作室

僅當 DE 在正在調試的程式的位址空間中運行時,才需要實現此方法。 否則,此方法應返回`S_FALSE`。

呼叫此方法時,如果尚未為[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面的此實例發送[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)事件物件,以及[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)和[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)事件物件,則 DE 必須發送 IDebugEngineCreateEvent2 事件物件。 如果`dwReason`參數`ATTACH_REASON_LAUNCH`為 ,則發送[IDebugentryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)事件物件。

DE`IDebugProgram2`必須在[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件物件提供的[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)對象上調用[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法,並且必須將該程式的 GUID 儲存在 DE 實現的物件的實例數據中。

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
