---
description: 這個方法會略過指定數目的 IDebugObject 元素。
title: IEnumDebugObjects：： Skip |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 962083242b5b178ddf39e21328917d09dc0ed09a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224638"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
這個方法會略過指定的元素數目。

## <a name="syntax"></a>語法

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   [In] uint celt
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
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
