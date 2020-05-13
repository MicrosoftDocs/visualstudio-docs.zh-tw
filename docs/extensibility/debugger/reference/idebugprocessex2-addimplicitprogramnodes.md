---
title: IDebugProcessEx2::添加隱式程序節點 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 113c81e95e7384be04b7e02a5c58cd2cad7c9c6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723404"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
此方法為指定的每個調試引擎 (DE) 添加一個程式節點。

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
[在]`GUID`用於啟動程式的 DE 的 DE(假定用於添加其自己的程式節點)。

`rgguidSpecificEngines`\
[在]`GUID`要為其添加程式節點的 D 陣列。

`celtSpecificEngines`\
[在]陣列中的`rgguidSpecificEngines``GUID`s 數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
- [Program Nodes](../../../extensibility/debugger/program-nodes.md)將添加在`rgguidSpecificEngines`中列出的每個 DE 的程式節點 - 不`guidLaunchingEngine`包括啟動引擎(如中給出的),假定在啟動程式時添加自己的程式節點。

## <a name="see-also"></a>另請參閱
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [程式節點](../../../extensibility/debugger/program-nodes.md)
