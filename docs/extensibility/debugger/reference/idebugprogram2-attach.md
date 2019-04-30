---
title: IDebugProgram2::Attach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c8cf4f3f5978744c38690681b4555f59cafd106
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870680"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
將附加至程式。

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

#### <a name="parameters"></a>參數
 `pCallback`

 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)用於偵錯事件通知的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 下表顯示一些可能的錯誤碼。

|值|描述|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|偵錯工具已附加指定的程式。|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|附加程序期間，發生安全性違規。|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面程式無法附加至偵錯工具。|

## <a name="remarks"></a>備註
 偵錯引擎 (DE) 永遠不會呼叫此方法來附加至程式。 DE 會在程式的位址空間，如果[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)呼叫方法。 DE 執行中工作階段偵錯管理員 (SDM) 位址空間，如果[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)呼叫方法。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)