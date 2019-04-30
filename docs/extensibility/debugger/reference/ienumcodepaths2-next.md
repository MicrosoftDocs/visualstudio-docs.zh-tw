---
title: IEnumCodePaths2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Next
helpviewer_keywords:
- IEnumCodePaths2::Next
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 803e8208ff1838c61da844b39d1423e8f99331cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915094"
---
# <a name="ienumcodepaths2next"></a>IEnumCodePaths2::Next
從列舉中傳回下的一個項目集。

## <a name="syntax"></a>語法

```cpp
HRESULT Next(
   ULONG       celt,
   CODE_PATH** rgelt,
   ULONG*      pceltFetched
);
```

```csharp
int Next(
   uint        celt,
   CODE_PATH[] rgelt,
   ref uint    pceltFetched
);
```

#### <a name="parameters"></a>參數
 `celt`

 [in]若要擷取的元素數目。 也會指定的大小上限`rgelt`陣列。

 `rgelt`

 [in、 out]陣列[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)来填入的項目。

 `pceltFetched`

 [out]傳回的項目數中實際傳回`rgelt`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`更少的項目要求的數目可能會傳回; 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)