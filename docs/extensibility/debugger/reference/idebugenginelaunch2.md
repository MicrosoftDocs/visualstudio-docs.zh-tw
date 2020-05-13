---
title: IDebugEngineLaunch2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730501"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
除錯引擎 (DE) 用於啟動和終止程式。

## <a name="syntax"></a>語法

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>實施者說明
 如果此介面具有啟動不能完全由自定義埠處理的進程的特殊要求,則此介面由自定義 DE 實現。 當 DE 是解釋器的一部分,並且正在調試的過程是一個腳本時,通常就是這種情況:首先需要啟動解釋器,然後載入和啟動腳本。 埠可以啟動解釋器,但腳本可能需要特殊處理(這是 DE 具有角色的位置)。 僅當存在啟動自定義埠無法處理的程式的唯一要求時,才會實現此介面。

## <a name="notes-for-callers"></a>通話備註
 如果 SDM 可以從[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面(使用查詢介面)獲取此介面,會話調試管理員 (SDM) 會調用此介面。 如果可以獲取此介面,SDM 知道 DE 具有特殊要求,並調用此介面啟動程式,而不是讓埠啟動它。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugEngineLaunch2`。

|方法|描述|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|通過DE啟動進程。|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|恢復進程執行。|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|確定是否可以終止進程。|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|終止進程。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
