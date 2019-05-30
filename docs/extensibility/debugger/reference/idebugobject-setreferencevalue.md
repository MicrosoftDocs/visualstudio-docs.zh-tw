---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aaef4eb96942789bd3f574e6eeddcd3500ae6ee9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349944"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
設定參考值，這個物件。

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
[in][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件，表示新的參考值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 此方法會進行這[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件中指定之物件的值參考`pObject`參數，白白丟掉的任何先前的參考。 請注意這個`IDebugObject`物件必須已經是參考型別。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)