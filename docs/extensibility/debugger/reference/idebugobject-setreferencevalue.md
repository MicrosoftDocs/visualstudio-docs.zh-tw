---
description: 設定這個物件的參考值。
title: IDebugObject：： SetReferenceValue |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a65c14d4122ac6d877573822b4fa8be1cb6cdd1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054110"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
設定這個物件的參考值。

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
在代表新參考值的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會讓這個 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件參考參數中提供的物件值，並擲回 `pObject` 任何先前的參考。 請注意，這個 `IDebugObject` 物件必須已經是參考型別。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
