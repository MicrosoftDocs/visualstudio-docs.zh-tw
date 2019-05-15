---
title: IDebugArrayObject::GetRank |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aabaaed13de191e4e0ee8d8d0e8422d3df144210
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615218"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
取得陣列，也就是維度數目的順位。

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
[out]傳回順位。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 使用[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)方法來擷取每個維度的陣列物件的大小。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)