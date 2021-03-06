---
description: 這個方法會為每個偵錯工具新增程式節點， (DE) 指定。
title: IDebugProcessEx2：： AddImplicitProgramNodes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 30e5943ca0326a05b98b9fb833004c0ba7e342d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076390"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
這個方法會為每個偵錯工具新增程式節點， (DE) 指定。

## <a name="syntax"></a>語法

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>參數
`guidLaunchingEngine`\
在 `GUID` 要用來啟動程式 (的 DE，並假設為) 加入自己的程式節點。

`rgguidSpecificEngines`\
在 `GUID`將新增程式節點的 DEs 陣列。

`celtSpecificEngines`\
在 `GUID`陣列中的數目 `rgguidSpecificEngines` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
- 系統會為中所列的每個取消加入[程式節點](../../../extensibility/debugger/program-nodes.md)， `rgguidSpecificEngines` 包括) 中所指定的啟動引擎 (`guidLaunchingEngine` ，這會在啟動程式時，假設要加入自己的程式節點。

## <a name="see-also"></a>另請參閱
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [程式節點](../../../extensibility/debugger/program-nodes.md)
