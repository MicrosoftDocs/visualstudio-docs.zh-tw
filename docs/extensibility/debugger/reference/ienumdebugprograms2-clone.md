---
title: IEnumDebugPrograms2：： Clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Clone
helpviewer_keywords:
- IEnumDebugPrograms2::Clone
ms.assetid: 880846c2-39d3-45cd-85c3-ad5409a3710f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38927f6b81c2cc00107bc06125343001079d0aee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846630"
---
# <a name="ienumdebugprograms2clone"></a>IEnumDebugPrograms2::Clone
傳回目前列舉的複本作為個別的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT Clone(
   IEnumDebugPrograms2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPrograms2 ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
擴展傳回這個列舉的複本作為個別的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉的複本在呼叫這個方法時，的狀態與原始的相同。 不過，複本和原始的狀態是分開的，而且可以個別變更。

## <a name="see-also"></a>另請參閱
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
