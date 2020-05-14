---
title: BP_COND_STYLE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738108"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
指定掛起和綁定斷點的斷點條件樣式。

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

## <a name="fields"></a>欄位
`BP_COND_NONE`\
到達斷點位置時觸發斷點。 未指定斷點條件。

`BP_COND_WHEN_TRUE`\
僅當與斷點關聯的條件表達式計算到`true`時,才觸發斷點。

`BP_COND_WHEN_CHANGED`\
僅當與斷點關聯的條件表達式的值與其以前的計算相比發生更改時,才觸發斷點。

## <a name="remarks"></a>備註
用於[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)結構`styleCondition`的成員。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
