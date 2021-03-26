---
description: 當程式附加至時，debug engine 會將這個介面傳送 (DE) 至會話 debug manager (SDM) 。
title: IDebugProgramCreateEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1fb183bfc11cb3e2711d83c7cb5f18cbe908d8e5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084346"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
當程式附加至時，debug engine 會將這個介面傳送 (DE) 至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 取消或自訂埠供應商會執行這個介面，以報告程式已建立，通常是在程式連接時。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 `QueryInterface` 方法來存取 `IDebugEvent2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 取消或自訂埠供應商會建立並傳送此事件物件，以報告程式的建立。 當它附加至正在進行偵錯工具的程式時，會使用由 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送此事件。 自訂埠供應商會使用 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 介面傳送此事件。

## <a name="remarks"></a>備註
 取消或自訂埠供應商會藉由呼叫[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)來發佈新的[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)介面。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
