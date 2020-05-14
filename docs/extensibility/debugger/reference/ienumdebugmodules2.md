---
title: IEnum調試模組2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 612285aa4d5a249c0f922ccae88d98a7df83187b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716441"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
此介面枚舉模組清單。

## <a name="syntax"></a>語法

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示為程式載入的模組清單。

## <a name="notes-for-callers"></a>通話備註
 可視化工作室調用[EnumModule](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugModules2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|在枚舉序列中檢索指定數量的模組。|
|[跳](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|在枚舉序列中跳過指定數量的模組。|
|[重設](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|獲取模組數。|

## <a name="remarks"></a>備註
 Visual Studio 主要使用此介面更新 **「模組」** 視窗。

 為了在 Visual Studio 中調試,程式是一個邏輯代碼指令序列,可以跨越模組邊界,因此需要單個[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面的模組清單。 清單中的第一個模組通常包含關聯程式的初始入口點。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
