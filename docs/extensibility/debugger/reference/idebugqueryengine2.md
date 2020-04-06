---
title: IDebug查詢引擎2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720661"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
此介面允許工作階段除錯管理員 (SDM) 檢索表示除錯引擎 (DE) 的介面。

## <a name="syntax"></a>語法

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 在實現最常見的 DE 介面的物件(如[IDebug Program2、IDebugThread2](../../../extensibility/debugger/reference/idebugprogram2.md)和[IDebugStackFrame2)](../../../extensibility/debugger/reference/idebugstackframe2.md)上實現此介面,以便允許訪問 DE 本身[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)的[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面。

## <a name="notes-for-callers"></a>通話備註
 在典型的 DE 介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugQueryEngine2`。

|方法|描述|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|獲取自定義除錯引擎 (DE) 介面。|

## <a name="remarks"></a>備註
 此介面通常在實現[IDebug Program2](../../../extensibility/debugger/reference/idebugprogram2.md)介面的物件中實現,以支援按因果關係順序執行函數;也就是說,當調試器退出函數時,要執行的下一個函數可能不是堆疊上的上一個函數,而是另一個線程中的函數。 有關「因果關係」的定義,請參閱[可視化工作室調試器詞彙表](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
