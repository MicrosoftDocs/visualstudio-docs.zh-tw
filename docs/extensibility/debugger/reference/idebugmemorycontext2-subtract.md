---
title: IDebug記憶體上下文2::減去 |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c858beb8c3f9f587633dbae8b3b1fe73fd789663
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727443"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
從當前上下文中減去指定值並返回新上下文。

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
[在]要減少的記憶體位元組數。

`ppMemCxt`\
[出]返回新的[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 記憶體上下文是位址,因此從位址中減去值會產生需要新上下文介面的新位址。

 此方法必須始終生成新上下文,即使生成的位址位於與此上下文關聯的記憶體空間之外也是如此。 唯一的例外是,如果無法為新上下文分配記憶體,或者是否`ppMemCxt`為空值(這是一個錯誤)。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
