---
description: 這個方法會在指定名稱的情況下尋找別名。
title: IDebugBinder3：： FindAlias |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9958c1c2b93d6547f1f3453bafc9e331f9061844
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089052"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
這個方法會在指定名稱的情況下尋找別名。 這會搜尋程式中的所有別名。

## <a name="syntax"></a>語法

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>參數
`pcstrName`\
在要尋找的別名名稱。

`ppAlias`\
擴展如果 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 介面所代表的任何) ，就會找到別名 (。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則 `S_FALSE` 會傳回 (如果找不到別名) 或錯誤碼。

## <a name="remarks"></a>備註
 在呼叫之前，這個方法會將目的地物件初始化為 null：然後，它會在之後測試是否有 null 值，以判斷是否找到別名。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
