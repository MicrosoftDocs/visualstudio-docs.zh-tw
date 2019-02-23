---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70ab3655d27e810b3c05d0e0e81d81bc15a26950
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685855"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
指定中斷點條件樣式暫止和繫結中斷點。

## <a name="syntax"></a>語法

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="members"></a>成員
當到達中斷點的位置時，則 BP_COND_NONE 就會引發中斷點。 沒有指定中斷點條件。

BP_COND_WHEN_TRUE 在條件運算式與中斷點相關聯的時評估為僅，就會引發中斷點`true`。

BP_COND_WHEN_CHANGED 引發中斷點與中斷點相關聯的條件式運算式的值時，才已經從其先前的評估。

## <a name="remarks"></a>備註
用於`styleCondition`隸屬[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)結構。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
