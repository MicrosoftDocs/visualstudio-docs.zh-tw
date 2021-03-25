---
description: 從錯誤中斷點列舉傳回下一組元素。
title: IEnumDebugErrorBreakpoints2：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2::Next
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Next
ms.assetid: 6a3dee11-5267-4d77-9e28-6a38413ba70b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02a96c6f6ea27eb7c80d97700395026663bd4a00
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052966"
---
# <a name="ienumdebugerrorbreakpoints2next"></a>IEnumDebugErrorBreakpoints2::Next
傳回列舉中的下一組元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Next(
   ULONG                    celt,
   IDebugErrorBreakpoint2** rgelt,
   ULONG*                   pceltFetched
);
```

```csharp
int Next(
   uint                     celt,
   IDebugErrorBreakpoint2[] rgelt,
   ref uint                 pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
在要取出的元素數目。 也指定陣列的大小上限 `rgelt` 。

`rgelt`\
[in，out]要填入的 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 元素陣列。

`pceltFetched`\
擴展傳回實際傳回的元素數目 `rgelt` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果可以傳回小於所要求的元素數目，則傳回，否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
