---
description: 取得陣列的維度。
title: IDebugArrayObject：： GetDimensions |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5bb935ea4aba6ab6ebd0a39f8dfc8d539d6555c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158679"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
取得陣列的維度。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>參數
`dwCount`\
在要取出的維度數目。

`dwDimensions`\
[in，out]填入每個維度大小的陣列。 `dwCount` 指定陣列的大小上限 `dwDimensions` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 多維度陣列的每個維度可以有不同的大小。 例如，假設有三維陣列 `myarray[3][2][6]` ，這個方法會以 `dwDimensions` 該順序傳回參數中的3、2和6。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
