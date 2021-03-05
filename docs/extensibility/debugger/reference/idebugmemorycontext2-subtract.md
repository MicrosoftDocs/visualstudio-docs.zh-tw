---
description: 從目前內容減去指定的值，並傳回新的內容。
title: IDebugMemoryCoNtext2：：減法 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d77a0fcd4d791eefe98ae908bdf86ba49bec519
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165003"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
從目前內容減去指定的值，並傳回新的內容。

## <a name="syntax"></a>語法

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>參數
`dwCount`\
在要遞減的記憶體位元組數目。

`ppMemCxt`\
擴展傳回新的 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 記憶體內容是一種位址，因此從位址減去值會產生新的位址，該位址需要新的內容介面。

 即使產生的位址超出與此內容相關聯的記憶體空間，這個方法也一定會產生新的內容。 唯一的例外狀況是，如果無法配置新內容的記憶體，或 `ppMemCxt` 為 null 值 (這是) 錯誤。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
