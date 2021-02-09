---
title: IDebugMemoryCoNtext2：： Compare |Microsoft Docs
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e54a2bf7cd37b411dbc2d18d23a3466a4b47ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851201"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
以比較旗標所指定的方式，將記憶體內容與指定陣列中的每個內容進行比較，並傳回符合之第一個內容的索引。

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
在 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) 列舉中的值，這個值會決定比較的類型。

`rgpMemoryContextSet`\
在要比較之 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 物件的參考陣列。

`dwMemoryContextSetLen`\
在陣列中的內容數目 `rgpMemoryContextSet` 。

`pdwMemoryContext`\
擴展傳回滿足比較的第一個記憶體內容的索引。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 `E_COMPARE_CANNOT_COMPARE`如果無法比較這兩個內容，則會傳回。

## <a name="remarks"></a>備註
 Debug engine (DE) 不需要支援所有類型的比較，但至少必須支援 `CONTEXT_EQUAL` 、 `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` 和 `CONTEXT_SAME_SCOPE` 。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
