---
description: 將指定的值加入至目前的內容，並傳回新的內容。
title: IDebugMemoryCoNtext2：： Add |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48847a65a1c5b6f514a96e702b9d8e666ad09630
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076793"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
將指定的值加入至目前的內容，並傳回新的內容。

## <a name="syntax"></a>語法

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>參數
`dwCount`\
在要加入至目前內容的值。

`ppMemCxt`\
擴展傳回新的 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 記憶體內容是位址，因此將值新增至位址會產生新的位址，需要新的內容介面。

 即使產生的位址超出與此內容相關聯的記憶體空間，這個方法也一定會產生新的內容。 唯一的例外狀況是，如果無法配置新內容的記憶體，或 `ppMemCxt` 為 null 值 (這是) 錯誤。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
