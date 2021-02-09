---
title: IDebugMemoryBytes2：： WriteAt |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ff77985bca8772d92c3b90e7a727c0077137e24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909911"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
從指定的位址開始，寫入指定的記憶體位元組數目。

## <a name="syntax"></a>語法

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>參數
`pStartContext`\
在 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 物件，指定開始寫入位元組的位置。

`dwCount`\
在要寫入的位元組數目。

`rgbMemory`\
在要寫入的位元組。 此陣列假設為至少 `dwCount` 位元組大小。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則， `S_FALSE` 如果並非所有的位元組都可以寫入或傳回錯誤碼 (通常是 `E_FAIL`) 。

## <a name="remarks"></a>備註
 如果起始位址不在這個 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 物件所代表的記憶體視窗內，則不會進行寫入，而且 `E_FAIL` 會傳回錯誤碼，即使要寫入的數量與記憶體空間重迭也一樣。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
