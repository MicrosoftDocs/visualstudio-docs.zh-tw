---
title: IDebugMethodfield::枚舉本地人 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727212"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
為方法的選定局部變數創建枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>參數
`pAddress`\
[在][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件,表示選擇從中獲取局部變數的上下文或作用域的調試位址。

`ppLocals`\
[出]返回表示局部變數清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件;否則,如果沒有局部變數,則返回 null 值。

## <a name="return-value"></a>傳回值
如果成功,則返回S_OK或返回S_FALSE如果沒有局部變數。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
僅枚舉在包含給定調試位址的塊中定義的變數。 如果需要所有局部變數(包括任何編譯器生成的局部變數),請調用[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)方法。

方法可以包含多個範圍上下文或塊。 例如,以下精心設計的方法包含三個作用域,兩個內部塊和方法體本身。

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)物件`func`表示 方法本身。 例如,`EnumLocals`使用[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)設置為`Inner Scope 1`位址調用方法將返回`temp1`包含變數的 枚舉。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
