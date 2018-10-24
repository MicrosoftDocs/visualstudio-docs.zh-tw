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
ms.openlocfilehash: 20981c744408e8d25e6e851c39532db939c71b2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939953"
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