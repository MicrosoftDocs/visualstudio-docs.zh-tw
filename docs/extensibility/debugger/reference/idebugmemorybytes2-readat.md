---
title: IDebug記憶位元組2::閱讀AT |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727529"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
從給定位置開始讀取位元組序列。

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
[在][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件,指定從何處開始讀取位元組。

`dwCount`\
[在]要讀取的位元組數。 還指定陣列的長度`rgbMemory`。

`rgbMemory`\
[進出]填充的位元組實際讀取。

`pdwRead`\
[出]返回實際讀取的連續位元組數。

`pdwUnreadable`\
[進出]返回不可讀位元組的數量。 如果用戶端對不可讀位元元數不感興趣,則可能是null值。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 如果請求 100 個字節,並且前 50 個字節可讀,則接下來的 20 個不可讀,其餘 30 個字節是可讀的,則此方法將返回:

 *`pdwRead`= 50

 *`pdwUnreadable`= 20

 在這種情況下,由於`*pdwRead + *pdwUnreadable < dwCount`調用方必須進行額外的調用才能讀取原始 100 個請求的剩餘 30`pStartContext`個字節, 並且參數中傳遞的[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)對象必須提前 70 個。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
