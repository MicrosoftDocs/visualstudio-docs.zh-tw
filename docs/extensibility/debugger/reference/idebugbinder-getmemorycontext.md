---
title: IDebugBinder:獲取記憶體上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d50126e26b836f7b53ee1abeb5c4988b74a2eed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735989"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
此方法將物件位置或記憶體位址轉換為記憶體上下文。

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
[在]描述要定位的物件的[IDebugField。](../../../extensibility/debugger/reference/idebugfield.md) 如果`NULL`,`dwConstant`則改用。

`dwConstant`\
[在]常量記憶體位址,如 0x5000。

`ppMemCxt`\
[出]返回表示物件位址或記憶體中位址的[IDebugMemoryMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
