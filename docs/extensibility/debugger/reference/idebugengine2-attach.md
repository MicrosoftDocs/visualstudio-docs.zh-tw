---
title: IDebugEngine2：： Attach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c045c68af91896323e4cb6422108de77ae76352
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948305"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
將 debug engine (DE) 附加至程式或程式。 當取消正在對 SDM 執行正在進行中的作業時，會話 debug manager (SDM) 。

## <a name="syntax"></a>語法

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>參數
`pProgram`\
在 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 物件的陣列，代表要附加的程式。 這些是埠程式。

`rgpProgramNodes`\
在代表程式節點的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 物件陣列，每個程式都有一個。 這個陣列中的程式節點，代表中的相同程式 `pProgram` 。 系統會提供程式節點，讓 DE 可以識別要附加的程式。

`celtPrograms`\
在和陣列中的程式和（或）程式節點數目 `pProgram` `rgpProgramNodes` 。

`pCallback`\
在要用來將 debug 事件傳送至 SDM 的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 物件。

`dwReason`\
在 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 列舉中的值，這個值會指定附加這些程式的原因。 如需詳細資訊，請參閱＜備註＞一節。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 附加至程式有三個原因，如下所示：

- `ATTACH_REASON_LAUNCH` 指出取消連接會附加至程式，因為使用者啟動了包含它的進程。

- `ATTACH_REASON_USER` 指出使用者已明確要求將 [取消] 附加至程式 (或包含程式) 的進程。

- `ATTACH_REASON_AUTO` 指出 DE 正在附加至特定程式，因為它已經在特定進程中進行其他程式的偵錯工具。 這也稱為自動附加。

  當呼叫這個方法時，DE 需要依序傳送這些事件：

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (如果尚未針對特定的 debug engine 實例傳送) 

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   此外，如果附加的原因是 `ATTACH_REASON_LAUNCH` ，則必須傳送 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) 事件。

   一旦 DE 取得 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 物件，而該物件對應至要進行偵錯工具，就可以查詢任何私用介面。

   在呼叫或所指定的陣列中程式節點的方法之前 `pProgram` `rgpProgramNodes` ，應該在代表程式節點的介面上啟用模擬（如有需要） `IDebugProgram2` 。 不過，通常不需要此步驟。 如需詳細資訊，請參閱 [安全性問題](../../../extensibility/debugger/security-issues.md)。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
