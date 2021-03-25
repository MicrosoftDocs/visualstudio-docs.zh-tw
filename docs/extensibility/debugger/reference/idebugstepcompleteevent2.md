---
description: 此介面是由 debug 引擎傳送 (當正在進行程式設計的程式在原始程式碼或語句或指令行中完成逐步執行、不進入一或多個步驟時，) 至會話 debug manager (SDM) 。
title: IDebugStepCompleteEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38791456500fc5996345314a0a779f5ccd03d940
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053187"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
此介面是由 debug 引擎傳送 (當正在進行程式設計的程式在原始程式碼或語句或指令行中完成逐步執行、不進入一或多個步驟時，) 至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行此介面來報告步驟作業的完成。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 「取消」會建立並傳送此事件物件，以報告步驟作業的完成。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="remarks"></a>備註
 完成此步驟之後，所要進行的程式開發程式就會暫停一次，而 IDE 會更新其所有視窗。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
