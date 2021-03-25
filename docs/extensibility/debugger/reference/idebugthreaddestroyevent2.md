---
description: 此介面是由偵錯工具引擎傳送 (當執行緒已執行完成時，將) 還原為會話 debug manager (SDM) 。
title: IDebugThreadDestroyEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2
helpviewer_keywords:
- IDebugThreadDestroyEvent2
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e97ad58a74c260703769dae83882d627c36c1d46
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086868"
---
# <a name="idebugthreaddestroyevent2"></a>IDebugThreadDestroyEvent2
此介面是由偵錯工具引擎傳送 (當執行緒已執行完成時，將) 還原為會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugThreadDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行此介面來報告執行緒已結束。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 DE 會建立並傳送此事件物件，以報告執行緒已結束。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugThreadDestroyEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|取得執行緒的結束代碼。|

## <a name="remarks"></a>備註
 Visual Studio 使用此事件來更新 [ **執行緒** ] 視窗。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
