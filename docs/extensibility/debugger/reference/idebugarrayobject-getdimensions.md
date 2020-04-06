---
title: IDebugarray物件:獲取維度 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 527f79724aeac0de58d0ae63c9c2408ed2eca9ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736170"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
獲取陣列的尺寸。

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
[在]要檢索的維度數。

`dwDimensions`\
[進出]填充每個維度大小的陣列。 `dwCount`指定`dwDimensions`數位的最大大小。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 多維陣組可以為每個維度具有不同的大小。 例如,給定三維陣列`myarray[3][2][6]`,此方法將按該順序返回參數中的`dwDimensions`3、2 和 6。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
