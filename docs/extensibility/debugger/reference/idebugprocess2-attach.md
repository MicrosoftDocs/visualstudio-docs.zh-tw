---
title: IDebugProcess2::附加 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724188"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
將會話調試管理員 (SDM) 附加到進程。

## <a name="syntax"></a>語法

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>參數
`pCallback`\
[在]用於調試事件通知的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件。

`rgguidSpecificEngines`\
[在]用於調試進程中運行的程式的調試引擎 GUID 陣列。 此參數可以是空值。 有關詳細資訊,請參閱備註。

`celtSpecificEngines`\
[在]陣列中的`rgguidSpecificEngines`除錯引擎數`rghrEngineAttach`和陣列的大小。

`rghrEngineAttach`\
[進出]調試引擎返回的 HRESULT 代碼陣列。 此陣列的大小在`celtSpecificEngines`參數中指定。 每個代碼通常是或`S_OK``S_ATTACH_DEFERRED`。 後者表示 DE 當前未附加到任何程式。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 下表顯示了其他可能的值。

|值|描述|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的程序已附加到除錯器。|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|在附加過程中發生了安全衝突。|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面進程無法附加到除錯器。|

## <a name="remarks"></a>備註
 附加到行程將 SDM 附加到該行程中運行的所有程式,這些程式`rgguidSpecificEngines`可以由 陣列中指定的調試引擎 (DE) 調試。 將`rgguidSpecificEngines`參數設定為 null 值`GUID_NULL`,或在陣列中包括附加到行程中的所有程式。

 進程中發生的所有調試事件都發送到給定的[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件。 當`IDebugEventCallback2`SDM 調用此方法時,將提供此物件。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
