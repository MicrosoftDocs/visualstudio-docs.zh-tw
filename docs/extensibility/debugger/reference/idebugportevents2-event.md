---
title: IDebugPortEvents2::Event | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ede9055f97a796e4e007914f68e370d4ff81420
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326751"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
這個方法會傳送事件，表示的建立和解構的處理序和連接埠上的程式。

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
[in][IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)表示偵錯伺服器物件 (一個針對每個執行個體[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]) 中發生的事件。

`pPort`\
[in][IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，表示發生事件的連接埠。

`pProcess`\
[in][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，表示發生事件的程序。

`pProgram`\
[in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示發生事件的程式。

`pEvent`\
[in][IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)可識別事件的物件。 可能的事件如下所示：

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
[in]事件的 GUID。 因為事件轉換成[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)之前呼叫這個方法，此識別碼可讓您更輕鬆地判斷哪些事件正在傳送。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)