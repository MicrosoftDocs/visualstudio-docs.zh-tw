---
title: IEnumDebugFrameInfo2：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Next
helpviewer_keywords:
- IEnumDebugFrameInfo2::Next
ms.assetid: 64a64eeb-5dea-4119-8a22-03771015d1e5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a5fe15c46066fdbc94b0b7f005ef7a06e1f10cc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716697"
---
# <a name="ienumdebugframeinfo2next"></a>IEnumDebugFrameInfo2::Next
傳回列舉中的下一組元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Next(
   ULONG       celt,
   FRAMEINFO** rgelt,
   ULONG*      pceltFetched
);
```

```csharp
int Next(
   uint        celt,
   FRAMEINFO[] rgelt,
   ref uint    pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
在要取出的元素數目。 也指定陣列的大小上限 `rgelt` 。

`rgelt`\
[in，out]要填入的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 元素陣列。

`pceltFetched`\
擴展傳回實際傳回的元素數目 `rgelt` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果可以傳回小於所要求的元素數目，則傳回，否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
