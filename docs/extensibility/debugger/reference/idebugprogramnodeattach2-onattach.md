---
description: 附加至相關聯的程式，或將附加進程延後至附加方法。
title: IDebugProgramNodeAttach2：： OnAttach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 334a8e4bdf559e2d39d52a03dcf1a849f73af3e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087258"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
附加至相關聯的程式，或將附加進程延後至 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法。

## <a name="syntax"></a>語法

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>參數
`guidProgramId`\
[in] `GUID` 指派給相關聯的程式。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不應該呼叫[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 在呼叫 [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法之前，會在附加程式期間呼叫這個方法。 `OnAttach`方法可以執行附加進程本身 (在這種情況下，這個方法會傳回 `S_FALSE`) ，或將附加進程延後至方法 `IDebugEngine2::Attach` (方法會傳回 `OnAttach` `S_OK`) 。 在任一事件中， `OnAttach` 方法都可以將 `GUID` 正在進行偵錯工具的設定為指定的 `GUID` 。

## <a name="see-also"></a>另請參閱
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
