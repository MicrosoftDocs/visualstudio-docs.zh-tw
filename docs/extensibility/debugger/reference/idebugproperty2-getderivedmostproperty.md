---
title: IDebug屬性2::獲取最派生的財產 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2086aded4361049d722ec36ba1d470ed8f7ac6e5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721499"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
獲取屬性的派生最源屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>參數
`ppDerivedMost`\
[出]返回表示派生最源屬性的[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。 如果沒有`S_GETDERIVEDMOST_NO_DERIVED_MOST`要檢索的派生最屬性,則返回。

## <a name="remarks"></a>備註
 例如,如果此屬性描述實現`ClassRoot`但實際上是`ClassDerived``ClassRoot`從 派生的物件的實例化,則此方法`ClassDerived`返回描述 該物件的[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
