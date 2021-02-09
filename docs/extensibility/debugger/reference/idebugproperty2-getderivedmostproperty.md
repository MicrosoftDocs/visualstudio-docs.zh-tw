---
title: IDebugProperty2：： GetDerivedMostProperty |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f91b00d2f448aea2f187e37813782ce568ad859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916037"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
取得屬性的衍生最多屬性。

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
擴展傳回 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 物件，這個物件表示衍生的最多屬性。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 `S_GETDERIVEDMOST_NO_DERIVED_MOST`如果沒有要抓取的衍生最多屬性，則會傳回。

## <a name="remarks"></a>備註
 例如，如果這個屬性描述的物件會執行， `ClassRoot` 但實際上是 `ClassDerived` 衍生自的具現化 `ClassRoot` ，則這個方法會傳回描述物件的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 物件 `ClassDerived` 。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
