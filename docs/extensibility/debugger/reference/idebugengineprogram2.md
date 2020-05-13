---
title: IDebugEngineProgram2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730307"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
此介面提供多線程調試支援。

## <a name="syntax"></a>語法

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎實現此介面以支援多個線程的同步調試。 此介面在實現[IDebug Program2](../../../extensibility/debugger/reference/idebugprogram2.md)介面的同一對象上實現。

## <a name="notes-for-callers"></a>通話備註
 使用[查詢介面](/cpp/atl/queryinterface)`IDebugProgram2`從介面獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugEngineProgram2`。

|方法|描述|
|------------|-----------------|
|[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|停止在此程式中運行的所有線程。|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|監視在給定線程上執行(或停止監視執行)。|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|允許(或不允許)在給定線程上進行表達式計算,即使程式已停止也是如此。|

## <a name="remarks"></a>備註
 Visual Studio 調用此介面以回應[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件,並設置程式的「線程步驟監視」和「線程表達式評估監視」狀態。 每當停止程式時,都會調用"停止";因此,每當程式停止時,都會調用["停止"。](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)此方法使程式有機會終止所有線程。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
