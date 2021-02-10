---
title: IDebugAlias：:D ispose |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 033d74be9548b6bdaaccfe567e99c1d94453bca5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944793"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
標記此別名以供移除。

## <a name="syntax"></a>語法

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 一旦呼叫這個方法之後，就無法再使用此別名。

## <a name="see-also"></a>另請參閱
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
