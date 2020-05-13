---
title: IDebugObject2::獲取別名 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53c72182b497e2b24d41a784c405d169c3db195f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726282"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
獲取與此物件關聯的別名(如果有)。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>參數
`ppAlias`\
[出]返回表示此物件的別名的[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)物件;否則,返回 null 值。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 使用對[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)方法的呼叫創建物件的別名。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
