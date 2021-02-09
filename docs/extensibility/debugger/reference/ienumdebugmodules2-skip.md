---
title: IEnumDebugModules2：： Skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Skip
helpviewer_keywords:
- IEnumDebugModules2::Skip
ms.assetid: 61dc42f4-8544-45bb-8da0-fb22cccec7da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a198cf442e1674f2ed378c78e1adff03cbe082fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932765"
---
# <a name="ienumdebugmodules2skip"></a>IEnumDebugModules2::Skip
略過指定的元素數目。

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
在要略過的元素數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果 `celt` 大於剩餘元素的數目，則傳回，否則傳回錯誤碼。

## <a name="remarks"></a>備註
 如果 `celt` 指定的值大於剩餘的元素數目，則列舉會設定為 end，並 `S_FALSE` 傳回。

## <a name="see-also"></a>另請參閱
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
