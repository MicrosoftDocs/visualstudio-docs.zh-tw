---
title: BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95e228a3aa0e96eedcf0413df7680e7a5664b707
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315413"
---
# <a name="bpstate"></a>BP_STATE
指定的繫結中斷點存在，也會指定是否已啟用。

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

## <a name="members"></a>成員
BPS_NONE  
指定任何中斷點存在。

BPS_DELETED  
指定已刪除的中斷點。

BPS_DISABLED  
指定停用中斷點。

BPS_ENABLED  
指定啟用中斷點。

## <a name="remarks"></a>備註
傳回從[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)方法。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
[列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
