---
title: IDebugPointerObject::GetBytes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a2c93e032175ce556d5504ed8b3f57dcf619a61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842700"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
取得指向為一系列的連續位元組的值。

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

#### <a name="parameters"></a>參數
 `dwStart`

 [in]以位元組為單位，從所指向之物件的開始位移。

 `dwCount`

 [in]要擷取的位元組數目。

 `pBytes`

 [in、 out]指向會填入值以一系列的連續的位元組陣列，從物件的指定位移處開始。

 `pdwBytes`

 [out]傳回實際擷取的位元組的數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 如果使用這個方法的指標，表示這個[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)指向基本型別或簡單基本型別 （也就是可以由簡單的一連串的位元組陣列） 的陣列。

## <a name="see-also"></a>另請參閱
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)