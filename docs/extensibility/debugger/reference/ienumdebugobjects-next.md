---
description: 這個方法會傳回列舉中的下一組 IDebugObject 元素。
title: IEnumDebugObjects：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 661d95f2196787502ab0ce144f6a7490c9911eca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064564"
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
這個方法會傳回列舉中的下一組元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Next(
   ULONG          celt,
   IDebugObject** rgelt,
   ULONG*         pceltFetched
);
```

```csharp
int Next(
   uint           celt,
   IDebugObject[] rgelt,
   ref uint       pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
在要取出的元素數目。 也指定陣列的大小上限 `rgelt` 。

`rgelt`\
[in，out]要填入的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 元素陣列。

`pceltFetched`\
擴展傳回實際傳回的元素數目 `rgelt` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果可以傳回小於所要求的元素數目，則傳回，否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
