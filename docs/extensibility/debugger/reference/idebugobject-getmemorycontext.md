---
title: IDebugObject：： GetMemoryCoNtext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2c7dbdace7c40ccba25cdce0306e6f0998489f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920781"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
取得表示物件值之位址的記憶體內容。

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
擴展傳回 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 物件，代表物件值的位址。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 傳回的記憶體內容會指定這個 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件所表示之值的位址。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
