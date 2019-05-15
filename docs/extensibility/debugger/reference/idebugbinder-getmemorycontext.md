---
title: IDebugBinder::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b1fe7c2b25a8931a449ac1ae2f4ba260f267bc22
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615052"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
這個方法會將記憶體內容的物件位置或記憶體位址。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>參數
`pField`\
[in][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述要尋找的物件。 如果`NULL`，然後使用`dwConstant`改。

`dwConstant`\
[in]常數的記憶體位址，例如 0x5000。

`ppMemCxt`\
[out]傳回[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)代表物件的位址或在記憶體中的位址的介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)