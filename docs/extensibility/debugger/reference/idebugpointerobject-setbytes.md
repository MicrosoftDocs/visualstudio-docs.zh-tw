---
title: IDebugPointer物件::設置位元組 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725509"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
設置從一系列連續位元組指向的值。

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
[在]從對象開頭指向的偏移(以位元組為單位)。

`dwCount`\
[在]要設置的位元組數。

`pBytes`\
[在]表示新值的位元組。 此值存儲在物件中,從給定偏移量開始。

`pdwBytes`\
[出]返回實際設置的位元組數。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 如果此[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)表示的指標指向基元類型或基元類型的簡單陣列(即可以由位元組的簡單序列表示的陣列),則使用此方法。 此`IDebugPointerObject`物件不能為空引用(它必須指向記憶體中的位址)。

## <a name="see-also"></a>另請參閱
- [取得位元組](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
