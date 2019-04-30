---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79f15102b5adae2112f4abdeeb68b80962895e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916795"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
將附加至相關聯的程式，或是遵照的附加程序[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。

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

#### <a name="parameters"></a>參數
 `guidProgramId`

 [in]`GUID`要指派給相關聯的程式。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`如果[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)不應該呼叫方法。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法是附加程序期間之前[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)呼叫方法。 `OnAttach`方法可以執行 attach 程序本身 (在此情況下，這個方法會傳回`S_FALSE`) 或延遲的附加程序`IDebugEngine2::Attach`方法 (`OnAttach`方法會傳回`S_OK`)。 在可能情況下，`OnAttach`方法可以設定`GUID`要進行偵錯程式的給定`GUID`。

## <a name="see-also"></a>另請參閱
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)