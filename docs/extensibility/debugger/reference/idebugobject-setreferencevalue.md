---
title: IDebugObject:設置參考值 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726372"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
設定此物件的引用值。

## <a name="syntax"></a>語法

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>參數
`pObject`\
[在]表示新引用值的[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md)。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法使此[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)`pObject`物件 對 參數中給出的物件的值的引用,並丟棄任何以前的引用。 請注意,此`IDebugObject`對象必須已經是引用類型。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
