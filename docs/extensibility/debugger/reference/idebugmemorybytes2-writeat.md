---
title: IDebug記憶位元組2::寫 at |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727526"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
從指定的位址開始,寫入指定的記憶體位元組數。

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
[在][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件,指定從何處開始寫入位元組。

`dwCount`\
[在]要寫入的位元組數。

`rgbMemory`\
[在]要寫入的位元組。 此陣列假定為大小中至少`dwCount`位元組。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,如果`S_FALSE`並非所有位元組都可以寫入或返回錯誤代碼(`E_FAIL`通常),則返回。

## <a name="remarks"></a>備註
 如果起始位址不在此[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)物件表示的記憶體視窗中,則不進行寫入並返回`E_FAIL`其錯誤代碼 -即使寫入量重疊到記憶體空間。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
