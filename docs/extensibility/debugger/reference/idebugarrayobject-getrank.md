---
title: IDebugArrayObject：： GetRank |Microsoft Docs
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
ms.openlocfilehash: 5fe662f6e6ed2db50fb905ad8918a7b7216853f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870099"
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
