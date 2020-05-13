---
title: IDebugProgram3::執行線程 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722655"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
執行調試器程式。 返回線程以向調試器提供有關使用者在執行程式時正在查看的線程的資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>參數
`pThread`\
[在][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 除錯器在停止後可以恢復執行的三種不同方式:

- 執行:取消任何上一步,並一直運行到下一個斷點等。

- 步驟:取消任何舊步驟,並一直運行到新步驟完成。

- 繼續:再次運行,並保留任何舊步驟處於活動狀態。

  在決定要取消`ExecuteOnThread`哪個步驟時,傳遞給的線程非常有用。 如果不知道線程,運行執行將取消所有步驟。 瞭解線程后,只需取消活動線程上的步驟。

## <a name="see-also"></a>另請參閱
- [執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
