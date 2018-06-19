---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a79c073048fe30a4abed069487ad09943253475
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115027"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> 已被取代。 請勿使用。

## <a name="syntax"></a>語法

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>傳回值

實作應該會一律傳回`E_NOTIMPL`。

## <a name="remarks"></a>備註

> [!WARNING]
> 自 Visual Studio 2005 中，這個方法已不再使用，應該會一律傳回`E_NOTIMPL`。

偵錯工具意外結束時，會呼叫這個方法。 呼叫這個方法時，DE 應該繼續程式，如同使用者中斷。 應該不傳送任何偵錯事件。 程式應該是可附加的偵錯工具的另一個執行個體的狀態中。

## <a name="see-also"></a>另請參閱

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)