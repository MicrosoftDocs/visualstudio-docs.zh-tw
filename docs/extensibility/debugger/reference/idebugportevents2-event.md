---
title: IDebugPort事件2::事件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931be468f6321250481aec79688f7f326abcfcac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725243"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
此方法發送表示在埠上創建和銷毀進程和程式的事件。

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
[在][IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)物件,表示發生該事件的每個實例都有一[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]個調試伺服器。

`pPort`\
[在]表示事件發生的埠的[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件。

`pProcess`\
[在][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件,表示事件發生的進程。

`pProgram`\
[在][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件,表示事件發生的程式。

`pEvent`\
[在]標識事件的[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)物件。 可能的事件如下:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
[在]事件的 GUID。 由於在調用此方法之前將事件強制轉換為[IDebugEvent2,](../../../extensibility/debugger/reference/idebugevent2.md)因此此識別符可以更輕鬆地確定正在發送的事件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
