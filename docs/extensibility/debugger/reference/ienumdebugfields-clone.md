---
title: IEnumDebugFields：： Clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5657e5db99bd062fa16aae9f9d8516bdbabc99f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727690"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
這個方法會傳回目前列舉的複本做為個別的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
脫銷傳回這個列舉的複本做為個別的物件。

## <a name="property-valuereturn-value"></a>屬性值/傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉的複本在呼叫這個方法時的狀態與原始的相同。 不過，複本和原始的狀態是分開的，而且可以個別變更。

## <a name="see-also"></a>請參閱
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)