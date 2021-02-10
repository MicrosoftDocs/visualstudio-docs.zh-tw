---
title: IEnumDebugModules2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dfcd594ab8764cedb8cbe2ea312675f884ae2338
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957149"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
此介面會列舉模組清單。

## <a name="syntax"></a>Syntax

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行這個介面，以代表為程式載入的模組清單。

## <a name="notes-for-callers"></a>呼叫者注意事項
 Visual Studio 會呼叫 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IEnumDebugModules2` 。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|抓取列舉序列中指定數目的模組。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|略過列舉序列中指定數目的模組。|
|[重設](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|將列舉順序重設為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|取得模組的數目。|

## <a name="remarks"></a>備註
 Visual Studio 使用此介面主要是用來更新 **模組** 視窗。

 為了在 Visual Studio 中進行偵錯工具，程式是程式碼指令的邏輯序列，可以跨模組界限，因此需要單一 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面的模組清單。 清單中的第一個模組通常包含相關程式的初始進入點。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
