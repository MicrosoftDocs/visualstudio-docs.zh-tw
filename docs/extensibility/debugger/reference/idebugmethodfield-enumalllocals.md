---
title: IDebugMethodfield::EnumAllLocals |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727339"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
為方法的所有局部變數創建枚舉器,包括編譯器內部生成的變數。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>參數
`pAddress`\
[在][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件表示方法中的調試位址,指向特定範圍或上下文。

`ppLocals`\
[出]返回表示指定作用域中所有局部變數清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件;否則,返回一個 null 值,指示沒有局部變數。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK或返回S_FALSE如果沒有局部變數。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 僅枚舉在包含給定調試位址的塊中定義的變數。 此方法包括任何編譯器生成的局部變數。 如果所需的全部是源中顯式定義的局部變數,請調用[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)方法。

 方法可以包含多個範圍上下文或塊。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
