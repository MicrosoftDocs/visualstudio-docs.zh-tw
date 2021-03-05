---
description: 取得設定屬性的方法。
title: IDebugPropertyField：： GetPropertySetter |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd787b88ae0e45de7afe944a79fdd0a788aa1449
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167928"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
取得設定屬性的方法。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPropertySetter( 
   IDebugMethodField** ppField
);
```

```csharp
int GetPropertySetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>參數
`ppField`\
擴展傳回代表設定屬性之方法的 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 若要取得取得屬性的方法，請呼叫 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
