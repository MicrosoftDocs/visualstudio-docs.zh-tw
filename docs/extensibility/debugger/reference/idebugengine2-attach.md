---
title: IDebugEngine2::附加 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731213"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
將除錯引擎 (DE) 附加到程式或程式。 當 DE 在行程中運行到 SDM 時,會話調試管理器 (SDM) 呼叫。

## <a name="syntax"></a>語法

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>參數
`pProgram`\
[在]表示要附加到的程式的[IDebug Program2](../../../extensibility/debugger/reference/idebugprogram2.md)物件的陣列。 這些是埠程式。

`rgpProgramNodes`\
[在]表示程式節點的[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件的陣列,每個程式一個。 此陣列中的程式節點表示與中的`pProgram`程式相同。 為程式節點提供,以便 DE 可以標識要附加到的程式。

`celtPrograms`\
[在]`pProgram`和`rgpProgramNodes`陣列中的程式和/或程式節點數。

`pCallback`\
[在]用於將除錯事件發送到 SDM 的[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件。

`dwReason`\
[在][ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)枚舉中指定附加這些程式的原因的值。 如需詳細資訊，請參閱＜備註＞一節。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 附加到程式有三個原因,如下所示:

- `ATTACH_REASON_LAUNCH`指示 DE 附加到程式,因為使用者啟動了包含它的進程。

- `ATTACH_REASON_USER`指示使用者已顯式請求 DE 附加到程式(或包含程式的進程)。

- `ATTACH_REASON_AUTO`指示 DE 附加到特定程式,因為它已在調試特定進程中的其他程式。 這也稱為自動附加。

  呼叫此方法時,DE 需要按順序傳送這些事件:

1. [IDebugEngineCreateEvent2(](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)如果尚未為除錯引擎的特定實體傳送)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   此外,如果附加的原因是`ATTACH_REASON_LAUNCH`,DE 需要發送[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)事件。

   一旦 DE 獲取與正在調試的程序對應的[IDebug ProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件,就可以查詢它的任何專用介面。

   在調用`pProgram``rgpProgramNodes`或 中給出的陣列中的程式節點的方法之前,應在表示程式`IDebugProgram2`節點的介面上啟用類比(如果需要)。 但是,通常不需要此步驟。 有關詳細資訊,請參閱[安全問題](../../../extensibility/debugger/security-issues.md)。

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
