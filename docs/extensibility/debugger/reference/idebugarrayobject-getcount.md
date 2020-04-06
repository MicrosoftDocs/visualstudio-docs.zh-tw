---
title: IDebugarray物件:獲取計數 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736206"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
獲取陣列中元素的計數。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>參數
`pdwElements`\
[出]返回計數。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法將數位物件的所有元素視為一維陣列,即使陣組對像是多維的。 例如,給定陣列`myarray[3][2][6]`,此方法`pdwElements`將在 參數中返回 36。 使用[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)方法一次檢索單個元素。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
