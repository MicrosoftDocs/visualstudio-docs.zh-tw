---
description: 建立此類別之函式的列舉值。
title: IDebugClassField：： EnumConstructors |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8efba9ecb25259b6aa4998a1f22fedf443c1281a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084970"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
建立此類別之函式的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`cMatch`\
在 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) 列舉中的值，這個值會指定要列舉的函式類型。

`ppEnum`\
擴展傳回表示函式清單的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件。 如果沒有任何函式，則傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，如果沒有任何函式則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉的每個元素都是描述函式方法的 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 物件。

 這些函式清單通常不包含編譯器所提供的預設的函式。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
