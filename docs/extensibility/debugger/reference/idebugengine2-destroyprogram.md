---
title: IDebugEngine2::DestroyProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f626005621604d367f5878e36899aa2ff46114ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875233"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
告知偵錯引擎 (DE) 指定的程式已終止 4mb，DE 應該清除至程式的所有參考，並傳送程式損毀的事件。

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

#### <a name="parameters"></a>參數
 `pProgram`

 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示已 4mb 終止程式。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 會呼叫這個方法之後，接著會傳送 DE [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)事件工作階段的偵錯管理員 (SDM)。

 不實作這個方法 (傳回`E_NOTIMPL`) 如果 DE 執行所偵錯之程式相同的程序中。 DE 在 SDM 相同的程序時，才會實作這個方法。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)