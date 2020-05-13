---
title: IDebugPointer欄位:獲取被引用欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 617711a611e6eb1ea162c3abd8ad2b793b4756cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725619"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
此方法返回此指針對象指向的物件類型。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>參數
`ppField`\
[出]傳回描述目標物件類型的[IDebugField。](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 例如,如果[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)物件指向整數,則此方法返回的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)類型將描述該整數類型。

## <a name="see-also"></a>另請參閱
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
