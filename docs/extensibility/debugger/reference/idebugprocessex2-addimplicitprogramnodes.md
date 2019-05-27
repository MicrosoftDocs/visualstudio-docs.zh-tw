---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 411b0b40d6c47f240472c82f727d955dda8df2df
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204085"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
這個方法會將每個偵錯引擎 (DE) 指定的程式 節點。

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
[in]`GUID`的規定是用來啟動程式 （並加入自己的程式節點會假設）。

`rgguidSpecificEngines`\
[in]陣列`GUID`的 DEs 節點將會新增的程式。

`celtSpecificEngines`\
[in]數目`GUID`中的 s`rgguidSpecificEngines`陣列。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
- [程式節點](../../../extensibility/debugger/program-nodes.md)將會加入每個 DE 列於`rgguidSpecificEngines`— 但不包括啟動引擎 (中所指定`guidLaunchingEngine`)，它會啟動程式時，將其本身的程式節點會假定為。

## <a name="see-also"></a>另請參閱
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [程式節點](../../../extensibility/debugger/program-nodes.md)