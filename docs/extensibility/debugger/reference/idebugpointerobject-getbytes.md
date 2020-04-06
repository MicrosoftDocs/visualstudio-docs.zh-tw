---
title: IDebugPointer物件::獲取位元組 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725511"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
獲取指向的一系列連續位元組的值。

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
[在]從對象開頭指向的偏移(以位元組為單位)。

`dwCount`\
[在]要檢索的位元組數。

`pBytes`\
[進出]以一系列連續位元組填充該值的陣列,從指向的物件的給定偏移開始。

`pdwBytes`\
[出]返回實際檢索的位元組數。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 如果此[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)表示的指標指向基元類型或基元類型的簡單陣列(即可以由位元組的簡單序列表示的陣列),則使用此方法。

## <a name="see-also"></a>另請參閱
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [設定位元組](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
