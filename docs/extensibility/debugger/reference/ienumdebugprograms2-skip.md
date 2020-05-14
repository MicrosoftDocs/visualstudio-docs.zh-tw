---
title: IEnum調試程式2::跳過 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Skip
helpviewer_keywords:
- IEnumDebugPrograms2::Skip
ms.assetid: b283858b-b375-4760-bfec-ab37de89958d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7459e6dae6487fbb9cec3e82a9d8ba01fbfef2a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715596"
---
# <a name="ienumdebugprograms2skip"></a>IEnumDebugPrograms2::Skip
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
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
