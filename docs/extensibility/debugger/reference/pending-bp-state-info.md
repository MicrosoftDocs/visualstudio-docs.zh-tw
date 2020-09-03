---
title: PENDING_BP_STATE_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d66ecc63e133a75148f06b59b8f1ccf61fe2658d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714083"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
包含已準備系結至程式碼位置之中斷點狀態的相關資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagPENDING_BP_STATE_INFO { 
   PENDING_BP_STATE       state;
   PENDING_BP_STATE_FLAGS flags;
} PENDING_BP_STATE_INFO;
```

```csharp
public struct PENDING_BP_STATE_INFO { 
   public uint state;
   public uint flags;
};
```

## <a name="members"></a>成員
 `state`\
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)列舉中的值，這個值會指定暫止中斷點的狀態。

 `flags`\
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)列舉中的旗標組合，指定中斷點是否虛擬化。

## <a name="remarks"></a>備註
 此結構會傳遞至其填入的 [>getstate](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) 方法。

## <a name="requirements"></a>需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
