---
title: BP_STATE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2aad05751a1e8abe89caaf2c2f6627e01e4f825
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931470"
---
# <a name="bp_state"></a>BP_STATE
指定系結中斷點是否存在，並指定是否已啟用。

## <a name="syntax"></a>Syntax

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
指定不存在任何中斷點。

`BPS_DELETED`\
指定中斷點已刪除。

`BPS_DISABLED`\
指定停用中斷點。

`BPS_ENABLED`\
指定中斷點已啟用。

## <a name="remarks"></a>備註
從 [>getstate](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) 方法傳回。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
