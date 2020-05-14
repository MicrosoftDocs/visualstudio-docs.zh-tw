---
title: IDebug記憶體上下文2::比較 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727499"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
以比較標誌指示的方式將記憶體上下文與給定陣列中的每個上下文進行比較,返回匹配的第一個上下文的索引。

## <a name="syntax"></a>語法

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>參數
`compare`\
[在][CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)枚舉中確定比較類型的值。

`rgpMemoryContextSet`\
[在]要與之比較的[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件的引用陣列。

`dwMemoryContextSetLen`\
[在]陣列中的`rgpMemoryContextSet`上下文數。

`pdwMemoryContext`\
[出]返回滿足比較的第一個記憶體上下文的索引。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_COMPARE_CANNOT_COMPARE`無法比較這兩個上下文,則返回。

## <a name="remarks"></a>備註
 除錯引擎 (DE) 不必支援所有類型的`CONTEXT_EQUAL`比較, 但必須至少`CONTEXT_LESS_THAN`支援`CONTEXT_GREATER_THAN``CONTEXT_SAME_SCOPE`與 。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
