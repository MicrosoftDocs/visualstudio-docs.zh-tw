---
title: IDebugPortEvents2：： Event |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcf8a827f09c1b8d0e83b92f7729635cbb0f7f18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896171"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
這個方法會傳送事件，以表示埠上的進程和程式的建立和終結。

## <a name="syntax"></a>語法

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>參數
`pMachine`\
在 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 物件，表示 debug server (發生事件的每個) 實例都有一個 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 。

`pPort`\
在代表事件發生所在之埠的 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 物件。

`pProcess`\
在 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 物件，表示發生事件的進程。

`pProgram`\
在 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 物件，表示發生事件的程式。

`pEvent`\
在識別事件的 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 物件。 可能的事件如下所示：

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
在事件的 GUID。 因為此事件會在呼叫這個方法之前轉換成 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) ，所以此識別碼可讓您更輕鬆地判斷正在傳送的事件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
