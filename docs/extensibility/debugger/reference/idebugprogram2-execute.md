---
title: IDebugProgram2::執行 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722978"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
繼續從已停止狀態運行此程式。 清除任何以前的執行狀態(如步驟),程式將再次開始執行。

> [!NOTE]
> 此方法已被取代。 請改用[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)方法。

## <a name="syntax"></a>語法

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 當使用者從其他程式線程中的停止狀態開始執行時,此程式將調用此方法。 當使用者從 IDE 中的 **「調試」** 選單中選擇 **「開始」** 命令時,也會調用此方法。 此方法的實現可能很簡單,如在程式中的當前線程上調用[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)方法。

> [!WARNING]
> 在處理此調用時,不要向[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)發送停止事件或立即(同步)事件;否則調試器可能會掛起。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)
