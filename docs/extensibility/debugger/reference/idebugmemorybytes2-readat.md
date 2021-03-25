---
description: 從指定位置開始讀取一連串的位元組。
title: IDebugMemoryBytes2：： ReadAt |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1fdcdf46f7f57f3ee6035bf9af8be5a7e99739f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076819"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
從指定位置開始讀取一連串的位元組。

## <a name="syntax"></a>語法

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>參數
`pStartContext`\
在 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 物件，指定開始讀取位元組的位置。

`dwCount`\
在要讀取的位元組數目。 也指定陣列的長度 `rgbMemory` 。

`rgbMemory`\
[in，out]以實際讀取的位元組填入的陣列。

`pdwRead`\
擴展傳回實際讀取的連續位元組數目。

`pdwUnreadable`\
[in，out]傳回無法讀取的位元組數目。 如果用戶端是以無法讀取的位元組數目感興趣，則可以是 null 值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果要求的是100個位元組，而第一個50是可讀取的，則接下來的20是無法讀取的，其餘的30則是可讀取的，這個方法會傳回：

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 在此情況下，因為 `*pdwRead + *pdwUnreadable < dwCount` 呼叫端必須進行額外的呼叫，以讀取原始100所要求的剩餘30個位元組，且參數中傳遞的 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 物件 `pStartContext` 必須是70。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
