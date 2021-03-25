---
description: 通知偵錯工具引擎 (DE) 指定的程式已被異常終止，而 DE 應該清除程式的所有參考，並傳送程式損毀事件。
title: IDebugEngine2：:D estroyProgram |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0a58dd5893c3235ded9c7eeb5f5d47e3ddcb380
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093843"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
通知偵錯工具引擎 (DE) 指定的程式已被異常終止，而 DE 應該清除程式的所有參考，並傳送程式損毀事件。

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
在 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 物件，表示已被異常終止的程式。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法之後，會接著將 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 事件傳回給會話 debug MANAGER (SDM) 。

 如果在與所 `E_NOTIMPL` 要進行的程式相同的進程中執行刪除，則不會執行這個方法 (會傳回) 。 只有當 DE 在與 SDM 相同的進程中執行時，才會執行此方法。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
