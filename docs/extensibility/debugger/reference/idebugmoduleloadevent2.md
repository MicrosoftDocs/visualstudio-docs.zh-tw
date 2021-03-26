---
description: 當載入或卸載模組時，debug engine 會將這個介面傳送 (DE) 至會話 debug manager (SDM) 。
title: IDebugModuleLoadEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2
helpviewer_keywords:
- IDebugModuleLoadEvent2 interface
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6030e5962c0544a63b7b9658622447324a15792
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065355"
---
# <a name="idebugmoduleloadevent2"></a>IDebugModuleLoadEvent2
當載入或卸載模組時，debug engine 會將這個介面傳送 (DE) 至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugModuleLoadEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面，以報告已載入或卸載模組。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 「取消」會建立並傳送此事件物件，以報告已載入或卸載的模組。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugModuleLoadEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|取得正在載入或卸載的模組。|

## <a name="remarks"></a>備註
 Visual Studio 使用此事件讓 **模組** 視窗保持在最新狀態。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
