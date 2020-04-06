---
title: IDebugObject:獲取記憶體上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16427685765c1471fba3993743efc204cb99c367
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726664"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
獲取表示物件值位址的記憶體上下文。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>參數
`pContext`\
[出]返回表示物件值位址的[IDebugMemoryMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 返回的記憶體上下文指定此[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md)表示的值的位址。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
