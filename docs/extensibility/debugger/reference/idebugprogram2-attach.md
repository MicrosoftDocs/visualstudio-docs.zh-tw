---
title: IDebugProgram2::附加 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d0b182ba7a873816e3a7aa32d39beb2c63cc5ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723145"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
附加到程式。

## <a name="syntax"></a>語法

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>參數
`pCallback`\
[在]用於調試事件通知的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 下表顯示了一些可能的錯誤代碼。

|值|描述|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的程式已附加到除錯器。|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|在附加過程中發生了安全衝突。|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面程式無法附加到除錯器。|

## <a name="remarks"></a>備註
 除錯引擎 (DE) 從不呼叫此方法附加到程式。 如果 DE 在程式的位址空間中運行,則調用[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 如果 DE 在工作階段除錯管理員 (SDM) 位址空間中運行,則呼叫[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
