---
title: BP_STATE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2721028c0635af274174574e4a264546c1909778
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737808"
---
# <a name="bp_state"></a>BP_STATE
指定綁定斷點的存在,並指定是否啟用了該斷點。

## <a name="syntax"></a>語法

```cpp
enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
typedef DWORD BP_STATE;
```

```csharp
public enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>欄位
`BPS_NONE`\
指定不存在斷點。

`BPS_DELETED`\
指定斷點已被刪除。

`BPS_DISABLED`\
指定斷點已禁用。

`BPS_ENABLED`\
指定啟用斷點。

## <a name="remarks"></a>備註
從[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)方法返回。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [取得狀態](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
