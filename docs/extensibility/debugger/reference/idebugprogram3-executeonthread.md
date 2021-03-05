---
description: 執行偵錯工具。
title: IDebugProgram3：： ExecuteOnThread |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3d996fd7b8cda1d5e36322c85d49c9889dd66dd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145998"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
執行偵錯工具。 會傳回執行緒，以提供在執行程式時，使用者所要查看之執行緒的偵錯工具資訊。

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
在 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 有三種不同的方式可讓偵錯工具在停止之後繼續執行：

- 執行：取消任何先前的步驟，並執行到下一個中斷點等等。

- 步驟：取消任何舊的步驟，並執行直到新步驟完成為止。

- 繼續：再次執行，並讓任何舊步驟保持作用中狀態。

  當您決定要取消的步驟時，傳遞給的執行緒 `ExecuteOnThread` 會很有用。 如果您不知道執行緒，執行 execute 會取消所有步驟。 使用執行緒的知識，您只需要取消使用中線程上的步驟。

## <a name="see-also"></a>另請參閱
- [執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
