---
title: IDebugPointerObject：： GetBytes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1961aaf45478f25ed8eb55d8eda91a5c4eafc4dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852943"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
取得指向連續位元組序列的值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>參數
`dwStart`\
在從指向之物件的開頭算起的位移（以位元組為單位）。

`dwCount`\
在要取出的位元組數目。

`pBytes`\
[in，out]陣列，其值會以一系列連續位元組的形式填入，從指向之物件的給定位移開始。

`pdwBytes`\
擴展傳回實際取出的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果這個 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) 所代表的指標指向基本型別或基本類型的簡單陣列，則會使用這個方法，也就是可由) 的簡單位元組序清單示的陣列 (。

## <a name="see-also"></a>另請參閱
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
