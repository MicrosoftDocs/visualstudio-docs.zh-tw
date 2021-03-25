---
description: 取得與此物件相關聯的別名（如果有的話）。
title: IDebugObject2：： GetAlias |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2cbf4a84af4001519617a7e6306c4139e763aea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053785"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
取得與此物件相關聯的別名（如果有的話）。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>參數
`ppAlias`\
擴展傳回代表這個物件之別名的 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 物件;否則，會傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 使用 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) 方法的呼叫來建立物件的別名。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
