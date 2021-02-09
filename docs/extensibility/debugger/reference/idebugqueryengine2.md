---
title: IDebugQueryEngine2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b555ac218ceee1d376c9f7cf3c9df87f7c2e2da0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909770"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
此介面可讓會話 debug manager (SDM) 抓取表示 (DE) 之 debug 引擎的介面。

## <a name="syntax"></a>Syntax

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 會在執行最常見的 DE 介面 (（例如 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)、 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)和) [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) ）的物件上執行這個介面，以允許存取 DE 本身的 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 在一般的 DE 介面上呼叫 [QueryInterface](/cpp/atl/queryinterface) 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugQueryEngine2` 。

|方法|描述|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|取得自訂的 debug engine (DE) 介面。|

## <a name="remarks"></a>備註
 這個介面通常會在實 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面的物件中執行，以支援因果排序的逐步執行函式;也就是說，當偵錯工具跳出函式時，下一個要執行的函式可能不是堆疊上的前一個函式，而是另一個執行緒中的函式。 如需 "因果" 的定義，請參閱 [Visual Studio 偵錯工具詞彙](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
