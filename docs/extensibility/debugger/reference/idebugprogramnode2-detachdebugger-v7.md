---
title: IDebugProgramNode2::Detach調試器_V7 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722117"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> 廢棄。 請勿使用。

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

實現應始終返回`E_NOTIMPL`。

## <a name="remarks"></a>備註

> [!WARNING]
> 自 Visual Studio 2005 起,此方法不再使用`E_NOTIMPL`,應始終返回 。

當調試器意外退出時,將調用此方法。 調用此方法時,DE 應像使用者從程式分離時一樣恢復該程式。 不應再發送調試事件。 程序應處於一種狀態,可以從調試器的另一個實例附加該程式。

## <a name="see-also"></a>另請參閱

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
