---
title: IDebugClassField::EnumInterfacesImplemented |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a5c951ac4f6f33495dad4136a1a09c11e639e029
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335358"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
建立這個類別所實作之介面的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，代表實作的介面清單。 如果沒有介面，則傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，或如果沒有在這個類別上實作介面，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉型別的每個項目是[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)描述介面的物件。 請注意，非受控[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]程式碼不會使用介面當做離散實體讓這個方法永遠都會傳回 null 值的非受控[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]程式碼。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)