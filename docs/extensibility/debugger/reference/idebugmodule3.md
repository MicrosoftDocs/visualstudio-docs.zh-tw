---
title: IDebugModule3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726738"
---
# <a name="idebugmodule3"></a>IDebugModule3
此介面表示支援符號和 JustMyCode 狀態的備用位置的模組。

## <a name="syntax"></a>語法

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>實施者說明
 調試引擎 (DE) 實現此介面以支援符號的替代位置,並與 JustMyCode 狀態配合使用(有關"JustMyCode"的定義,請參閱[可視化工作室調試器術語表](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md))。

## <a name="notes-for-callers"></a>通話備註
 對[GetSymbolSearchSearchInfo 的](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)呼叫將返回此介面。 DE 使用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法將[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)介面發送到工作階段調試管理員 (SDM)。 此外,對[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) [介面上的查詢介面](/cpp/atl/queryinterface)的調用將返回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|返回搜索符號的路徑清單和搜索每個路徑的結果。|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|載入和初始化當前模組的符號。|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|返回指示模組是否表示使用者代碼的標誌。|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|指定是否應將模組視為用戶代碼。|

## <a name="remarks"></a>備註
 Visual Studio 是此介面的典型消費者。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
