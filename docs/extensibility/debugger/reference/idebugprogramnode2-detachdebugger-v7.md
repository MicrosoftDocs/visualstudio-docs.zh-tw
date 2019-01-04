---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 603c459d39f8141789b22955e916e3e8520214fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924146"
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

實作應該一律傳回`E_NOTIMPL`。

## <a name="remarks"></a>備註

> [!WARNING]
> 截至 Visual Studio 2005 中，這個方法不會再使用，並應該一律傳回`E_NOTIMPL`。

偵錯工具意外結束時，會呼叫這個方法。 呼叫這個方法時，DE 應該繼續程式，如同使用者已從它中斷連結。 應該不傳送任何偵錯事件。 程式應該要在其所在之可附加的偵錯工具的另一個執行個體的狀態。

## <a name="see-also"></a>另請參閱

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)