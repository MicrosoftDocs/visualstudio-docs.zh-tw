---
title: IDebugModule2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a43c7e7ed24da7d73784e20e9e998bdfe69cbd65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929742"
---
# <a name="idebugmodule2"></a>IDebugModule2
此介面代表模組，也就是程式的可執行單元，例如 DLL。

## <a name="syntax"></a>Syntax

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行此介面來代表模組，並提供該模組的相關資訊存取權。

## <a name="notes-for-callers"></a>呼叫者注意事項
 對 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) 的呼叫會傳回這個介面。 會將 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 介面傳送至會話 debug MANAGER (SDM) 使用 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 方法。

 這個介面也可以在 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構中傳回， (由 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)) 的呼叫所傳回。

- [接著](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) 也會傳回這個介面 ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) 會傳回 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) 介面) 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugModule2` 。

|方法|描述|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|取得描述此模組的 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 。|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|已過時。 請勿使用。 重載此模組的符號。|

## <a name="remarks"></a>備註
 模組資訊可以顯示在 IDE 的 [ **模組** ] 視窗中。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
