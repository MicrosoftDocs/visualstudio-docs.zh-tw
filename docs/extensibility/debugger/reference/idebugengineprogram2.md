---
description: 此介面提供多執行緒的調試支援。
title: IDebugEngineProgram2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e52ae6477b49325d4b8a4d81192fe2ecf736163
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092653"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
此介面提供多執行緒的調試支援。

## <a name="syntax"></a>Syntax

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 偵錯工具引擎會執行這個介面，以支援多個執行緒的同時偵錯工具。 此介面會在執行 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面的相同物件上進行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 使用 [QueryInterface](/cpp/atl/queryinterface) 從介面取得這個介面 `IDebugProgram2` 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugEngineProgram2` 。

|方法|描述|
|------------|-----------------|
|[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|停止在此程式中執行的所有線程。|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|監看執行 (或停止監看執行) 發生在指定的執行緒上。|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|允許 (或不允許在指定的執行緒上執行) 運算式評估，即使程式已停止也是如此。|

## <a name="remarks"></a>備註
 Visual Studio 會呼叫此介面來回應 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件，並設定程式的「監看式執行緒步驟」和「監看執行緒上的運算式評估」狀態。 每當程式停止時，就會呼叫[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ;這個方法可讓程式有機會終止所有線程。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
