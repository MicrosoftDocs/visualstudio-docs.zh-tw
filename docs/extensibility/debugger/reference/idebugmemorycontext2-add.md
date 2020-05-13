---
title: IDebug記憶體上下文2::添加 |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727478"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
將指定的值添加到當前上下文並返回新上下文。

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
[在]要添加到當前上下文的值。

`ppMemCxt`\
[出]返回新的[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 記憶體上下文是位址,因此向位址添加值會產生需要新上下文介面的新位址。

 此方法必須始終生成新上下文,即使生成的位址位於與此上下文關聯的記憶體空間之外也是如此。 唯一的例外是,如果無法為新上下文分配記憶體,或者是否`ppMemCxt`為空值(這是一個錯誤)。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
