---
description: 從一連串連續的位元組設定指向的值。
title: IDebugPointerObject：： SetBytes |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31feb63e4f9d246161ced3483f487b2877ee5e1e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169661"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
從一連串連續的位元組設定指向的值。

## <a name="syntax"></a>語法

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>參數
`dwStart`\
在從指向之物件的開頭算起的位移（以位元組為單位）。

`dwCount`\
在要設定的位元組數目。

`pBytes`\
在表示新值的位元組陣列。 此值會儲存在物件中，從指定的位移開始。

`pdwBytes`\
擴展傳回實際設定的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果這個 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) 所代表的指標指向基本型別或基本類型的簡單陣列，則會使用這個方法，也就是可由) 的簡單位元組序清單示的陣列 (。 此 `IDebugPointerObject` 物件不可以是 null 參考 (它必須指向記憶體) 中的位址。

## <a name="see-also"></a>另請參閱
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
