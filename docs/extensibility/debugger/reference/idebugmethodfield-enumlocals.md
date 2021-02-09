---
title: IDebugMethodField：： EnumLocals |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 98d6d7c4d9f1df0c7c4346792d841de574859619
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861149"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
為方法的選取區域變數建立枚舉器。

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
在 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 物件，代表用來選取要從中取得區域變數之內容或範圍的偵錯工具位址。

`ppLocals`\
擴展傳回 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件，代表區域變數的清單。否則，如果沒有任何區域變數，則會傳回 null 值。

## <a name="return-value"></a>傳回值
如果成功，會傳回 S_OK，如果沒有任何區域變數，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
只會列舉區塊內定義的變數，其中包含指定的 debug 位址。 如果需要所有的區域變數，包括任何編譯器產生的區域變數，請呼叫 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) 方法。

方法可以包含多個範圍內容或區塊。 例如，下列假設方法包含三個範圍：兩個內部區塊和方法主體本身。

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

[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)物件代表 `func` 方法本身。 `EnumLocals`例如，呼叫[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)設定為位址的方法會傳回 `Inner Scope 1` 包含變數的列舉 `temp1` 。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
