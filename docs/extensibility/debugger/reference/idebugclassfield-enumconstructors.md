---
title: IDebugClassField::枚舉器 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 607f4f4af3021389628fcc1be446ebbe95628b7c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734464"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
為此類的構造函數創建枚舉器。

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
[在][CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)枚舉中指定要枚舉構造函數的類型的值。

`ppEnum`\
[出]返回表示建構函數清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件。 如果沒有構造函數,則返回 null 值。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK或返回S_FALSE如果沒有構造函數。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 枚舉的每個元素都是描述構造函數方法的[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)物件。

 建構函數清單通常不包括編譯器提供的預設構造函數。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
