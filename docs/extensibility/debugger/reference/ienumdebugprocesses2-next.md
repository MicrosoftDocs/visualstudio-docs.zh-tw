---
title: IEnum調試進程2::下一個 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Next
helpviewer_keywords:
- IEnumDebugProcesses2::Next
ms.assetid: abef89eb-198b-49cd-a4c9-17bce6cac0e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbfab7f13160129249afe7139ef3c402ba9801ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715831"
---
# <a name="ienumdebugprocesses2next"></a>IEnumDebugProcesses2::Next
從枚舉返回下一組元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProcess2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProcess2[] rgelt,
   ref uint         pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
[在]要檢索的元素數。 還指定`rgelt`數位的最大大小。

`rgelt`\
[進出]要填充的[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)元素的陣列。

`pceltFetched`\
[出]返回中`rgelt`實際返回的元素數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果`S_FALSE`返回的元素數少於請求的元素數,則返回;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
