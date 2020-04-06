---
title: IEnumCodePath2::下一個 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Next
helpviewer_keywords:
- IEnumCodePaths2::Next
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e126fc916360d0cc992da5f17edecda7cb2ef41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717815"
---
# <a name="ienumcodepaths2next"></a>IEnumCodePaths2::Next
從枚舉返回下一組元素。

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

## <a name="parameters"></a>參數
`celt`\
[在]要檢索的元素數。 還指定`rgelt`數位的最大大小。

`rgelt`\
[進出]要填充[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)元素的陣列。

`pceltFetched`\
[出]返回中`rgelt`實際返回的元素數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果`S_FALSE`返回的元素數少於請求的元素數,則返回;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)
