---
description: 取得陣列的順位，也就是維度的數目。
title: IDebugArrayObject：： GetRank |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a246cda3f5b9395ae013b4bca9d4d27d6f8a5c1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158536"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
取得陣列的順位，也就是維度的數目。

## <a name="syntax"></a>語法

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>參數
`pdwRank`\
擴展傳回排名。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 您可以使用 [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) 方法來取出陣列物件的每個維度大小。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
