---
title: IDebugMethodField::EnumLocals |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a99fb1e0b8b32f98d06f34ac39b8dfd781cdc62
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211985"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
建立選取的本機變數之方法的列舉值。

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
[in][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件，表示選取的內容或範圍，從中取得區域變數的偵錯位址。

`ppLocals`\
[out]會傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示區域變數的清單; 如果沒有任何區域變數，否則會傳回 null 值。

## <a name="return-value"></a>傳回值
如果成功，會傳回 S_OK，或如果沒有任何區域變數，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
列舉只包含指定的偵錯位址區塊內定義的變數。 如果所有的區域變數，包括任何編譯器所產生的區域變數，則需要呼叫[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)方法。

一種方法可以包含多個範圍的內容或區塊。 例如，下列方法包含三個範圍、 兩個內部區塊和方法主體本身。

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

[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)物件表示`func`方法本身。 呼叫`EnumLocals`方法[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)設定為`Inner Scope 1`位址可讓您傳回列舉，其中包含`temp1`變數，例如。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
