---
title: IDebugEngine2::D微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce139dd22361d9914693cbe8ad723656ab7d4f26
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731105"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
通知除錯引擎 (DE), 指定的程式已終止,DE 應清除對程式的所有引用並發送程式銷毀事件。

## <a name="syntax"></a>語法

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>參數
`pProgram`\
[在][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件,表示已終止的程式。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 呼叫此方法後,DE 隨後將[IDebugProgram破壞事件2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)事件發送回工作階段調試管理員 (SDM)。

 如果 DE 與正在`E_NOTIMPL`調試 的程式在同一進程中運行,則此方法不會實現(返回)。 僅當 DE 與 SDM 在同一進程中運行時,才會實現此方法。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
