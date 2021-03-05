---
description: 將指定的值加入至目前的內容，並傳回新的內容。
title: IDebugMemoryCoNtext2：： Add |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59daddd38daff2f04f12bc0d1be4e06ec90cf723
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166420"
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
