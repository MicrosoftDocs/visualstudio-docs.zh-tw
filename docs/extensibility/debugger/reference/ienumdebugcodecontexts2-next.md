---
title: IEnumDebugCodeContexts2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Next
helpviewer_keywords:
- IEnumDebugCodeContexts2::Next
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 97083976a435605c32069051337c7fca4dca59e8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351067"
---
# <a name="ienumdebugcodecontexts2next"></a>IEnumDebugCodeContexts2::Next
從列舉中傳回下的一個項目集。

## <a name="syntax"></a>語法

```cpp
HRESULT Next(
   ULONG                celt,
   IDebugCodeContext2** rgelt,
   ULONG*               pceltFetched
);
```

```csharp
int Next(
   uint                 celt,
   IDebugCodeContext2[] rgelt,
   ref uint             pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
[in]若要擷取的元素數目。 也會指定的大小上限`rgelt`陣列。

`rgelt`\
[in、 out]陣列[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)来填入的項目。

`pceltFetched`\
[out]傳回的項目數中實際傳回`rgelt`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`更少的項目要求的數目可能會傳回; 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)