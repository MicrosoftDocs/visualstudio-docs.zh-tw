---
description: 將會話 debug manager (SDM) 附加至進程。
title: IDebugProcess2：： Attach |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73dbe76a32e67794736fd26595378485879b00b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161440"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
將會話 debug manager (SDM) 附加至進程。

## <a name="syntax"></a>語法

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>參數
`pCallback`\
在用於 debug 事件通知的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 物件。

`rgguidSpecificEngines`\
在用來在進程中執行的偵錯工具之偵錯工具的 Guid 陣列。 這個參數可以是 null 值。 如需詳細資訊，請參閱備註。

`celtSpecificEngines`\
在陣列中的偵錯工具引擎數目 `rgguidSpecificEngines` 以及陣列的大小 `rghrEngineAttach` 。

`rghrEngineAttach`\
[in，out]偵錯工具引擎所傳回的 HRESULT 代碼陣列。 這個陣列的大小是在參數中指定 `celtSpecificEngines` 。 每個程式碼通常是 `S_OK` 或 `S_ATTACH_DEFERRED` 。 後者表示 DE 目前未附加到任何程式。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 下表顯示其他可能的值。

|值|描述|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的進程已附加至偵錯工具。|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|附加程式期間發生安全性違規。|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面進程無法附加至偵錯工具。|

## <a name="remarks"></a>備註
 附加至處理常式會將 SDM 附加至在該進程中執行的所有程式，而這些程式可以由 debug 引擎進行調試 (DE) 陣列中所指定 `rgguidSpecificEngines` 。 將 `rgguidSpecificEngines` 參數設定為 null 值，或包含 `GUID_NULL` 在陣列中以附加至進程中的所有程式。

 在處理常式中發生的所有 debug 事件都會傳送至指定的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 物件。 `IDebugEventCallback2`當 SDM 呼叫這個方法時，會提供此物件。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
