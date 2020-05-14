---
title: IEnum調試程式2::下一個 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Next
helpviewer_keywords:
- IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 035af638b9504318a39e01f34ed32719d957896e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715626"
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
從枚舉返回下一組元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProgram2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProgram2[] rgelt,
   ref uint         pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
[在]要檢索的元素數。 還指定`rgelt`數位的最大大小。

`rgelt`\
[進出]要填充的[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)元素的陣列。

`pceltFetched`\
[出]返回中`rgelt`實際返回的元素數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果`S_FALSE`返回的元素數少於請求的元素數,則返回;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
