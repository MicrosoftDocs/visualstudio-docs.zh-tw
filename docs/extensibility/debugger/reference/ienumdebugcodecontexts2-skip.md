---
title: IEnumDebugCode密碼上下文2::跳過 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Skip
helpviewer_keywords:
- IEnumDebugCodeContexts2::Skip
ms.assetid: 3451a3eb-bf5b-4ec5-acc9-aa5a24363801
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6a1f63f5e3a6a84d6752707de5c81b4549085662
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717309"
---
# <a name="ienumdebugcodecontexts2skip"></a>IEnumDebugCodeContexts2::Skip
跳過指定數量的元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>參數
`celt`\
[在]要跳過的元素數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果`S_FALSE``celt`大於剩餘元素數,則返回;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 如果`celt`指定大於剩餘元素數的值,則枚舉將設置為末尾`S_FALSE`並返回。

## <a name="see-also"></a>另請參閱
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
