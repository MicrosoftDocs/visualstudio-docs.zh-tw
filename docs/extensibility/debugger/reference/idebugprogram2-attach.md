---
title: IDebugProgram2：： Attach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f42aa8ff646a62f7314887df4b38c648e2d84b31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931444"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
附加至程式。

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
在要用於偵錯工具事件通知的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 下表顯示一些可能的錯誤代碼。

|值|描述|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的程式已附加至偵錯工具。|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|附加程式期間發生安全性違規。|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面程式無法附加至偵錯工具。|

## <a name="remarks"></a>備註
 Debug engine (DE) 永遠不會呼叫這個方法來附加至程式。 如果在程式的位址空間中執行取消，則會呼叫 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法。 如果在會話 debug manager 的 (SDM) 位址空間中執行取消，則會呼叫 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
