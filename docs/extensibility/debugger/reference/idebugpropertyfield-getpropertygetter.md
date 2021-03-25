---
description: 取得取得屬性的方法。
title: IDebugPropertyField：： GetPropertyGetter |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddd7479f907ab305b7c0e0847bb7476b0c2c629c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058192"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
取得取得屬性的方法。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPropertyGetter( 
   IDebugMethodField** ppField
);
```

```cpp
int GetPropertyGetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>參數
`ppField`\
擴展傳回代表取得屬性之方法的 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 為了取得設定屬性的方法， [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) 會呼叫方法。

## <a name="see-also"></a>另請參閱
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
