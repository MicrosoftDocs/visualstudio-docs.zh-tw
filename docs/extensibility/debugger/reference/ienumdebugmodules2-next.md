---
title: IEnumDebugModules2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5ce512cde85dd305b2d9efb360d805eddbba40e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350295"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
從列舉中傳回下的一個項目集。

## <a name="syntax"></a>語法

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugModule2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugModule2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
[in]若要擷取的元素數目。 也會指定的大小上限`rgelt`陣列。

`rgelt`\
[in、 out]陣列[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)来填入的項目。

`pceltFetched`\
[out]傳回的項目數中實際傳回`rgelt`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`更少的項目要求的數目可能會傳回; 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)