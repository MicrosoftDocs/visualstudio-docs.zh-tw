---
title: IDebugObject:獲取大小 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8fd42abfc056c3b9e50d073ad335f72ac9022aa7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726565"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
獲取以位元組為單位的物件的大小。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSize( 
   UINT* pnSize
);
```

```csharp
int GetSize(
   out uint pnSize
);
```

## <a name="parameters"></a>參數
`pnSize`\
[出]返回大小(以位元組為單位)。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 使用[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)方法將值檢索為位元組序列。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
