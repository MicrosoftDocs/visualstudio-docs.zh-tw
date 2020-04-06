---
title: IDebugEngineProgram2::停止 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 286a448ee33f57d2e3a3282dc8d72b11a843a9c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730477"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
停止在此程式中運行的所有線程。

## <a name="syntax"></a>語法

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 在多程式環境中調試此程式時,將調用此方法。 當收到來自其他某個程式的停止事件時,此程式上調用此方法。 此方法的實現應該是異步的;也就是說,在此方法返回之前,不應要求停止所有線程。 此方法的實現可能非常簡單,例如在此程式中調用[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)方法。

 當程式停止時,實施者應發送[IDebugStopCompleteEvent2。](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md)

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
