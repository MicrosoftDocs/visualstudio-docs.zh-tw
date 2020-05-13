---
title: IDebugModule2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726902"
---
# <a name="idebugmodule2"></a>IDebugModule2
此介面表示一個模組,即程式的可執行單元,如 DLL。

## <a name="syntax"></a>語法

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示模組並提供對該模組資訊的訪問。

## <a name="notes-for-callers"></a>通話備註
 對[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)的調用將返回此介面。 DE 使用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法將[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)介面發送到工作階段調試管理員 (SDM)。

 此介面也可以在[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構中返回(通過呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)返回)。

- [接下來](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)還會返回此介面 ([枚舉模組](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)返回[IEnum DebugModule2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)介面)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugModule2`。

|方法|描述|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|獲取描述此模組[MODULE_INFO。](../../../extensibility/debugger/reference/module-info.md)|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|已過時。 請勿使用。 重新載入此模組的符號。|

## <a name="remarks"></a>備註
 模組資訊可以顯示在 IDE 的 **「模組」** 視窗中。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [取得模組](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
