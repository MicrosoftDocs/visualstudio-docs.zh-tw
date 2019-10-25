---
title: IEnumDebugFields：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 216ce9d49ba9de33307ad692787d6e6d36ee15c3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727654"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
這個方法會從列舉傳回下一組元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugField** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugField[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
在要取出的元素數目。 也會指定 `rgelt` 陣列的大小上限。

`rgelt`\
[in、out]要填入之[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)元素的陣列。

`pceltFetched`\
脫銷傳回 `rgelt` 中實際傳回的元素數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果可能傳回的專案數少於所要求的數目，則傳回 `S_FALSE`。否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)