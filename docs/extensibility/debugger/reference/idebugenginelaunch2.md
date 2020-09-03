---
title: IDebugEngineLaunch2 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730501"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
由 debug engine 使用 (DE) 來啟動和終止程式。

## <a name="syntax"></a>語法

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 如果這個介面具有啟動無法完全由自訂埠處理之進程的特殊需求，則會由自訂的 DE 實作為。 這種情況通常是因為 DE 是解譯器的一部分，而正在進行調試的進程是腳本：必須先啟動解譯器，然後載入和啟動腳本。 埠可以啟動解譯器，但腳本可能需要特殊處理 (也就是 DE 有角色) 。 只有在啟動自訂埠無法處理的程式時，才會執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 如果 SDM 可以從 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 介面取得這個介面， (使用 QueryInterface) ，則會話 debug manager 會呼叫這個介面 (sdm) 。 如果可以取得這個介面，則 SDM 知道 DE 具有特殊的需求，並呼叫此介面來啟動程式，而不是讓埠啟動它。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugEngineLaunch2` 。

|方法|描述|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|藉由 DE 來啟動處理常式。|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|繼續執行進程。|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|判斷是否可以終止進程。|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|終止進程。|

## <a name="requirements"></a>需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
