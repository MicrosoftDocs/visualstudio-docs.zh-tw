---
title: IDebugarray物件:獲取元素 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be06acbef93d8858557fea5bd7563168be2d28aa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736247"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
獲取陣列所有元素的枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]傳回允許枚舉所有元素的[IEnumDebug 物件物件](../../../extensibility/debugger/reference/ienumdebugobjects.md)。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 作為替代方法,請使用[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)和[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)方法遍越使用元素。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
