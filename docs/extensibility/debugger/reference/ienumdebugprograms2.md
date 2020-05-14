---
title: IEnum調試程式2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715574"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
此介面枚舉在當前調試會話中運行的程式。

## <a name="syntax"></a>語法

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面,以提供 DE 正在除錯的程式的清單。

## <a name="notes-for-callers"></a>通話備註
 Visual Studio 調用[枚舉程式](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)以獲取此介面。 [視覺工作室不使用枚舉程式](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugPrograms2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|在枚舉序列中檢索指定數量的程式。|
|[跳](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|在枚舉序列中跳過指定數量的程式。|
|[重設](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|獲取枚舉器中的程式數。|

## <a name="remarks"></a>備註
 Visual Studio 使用此介面:

- 填充**模組**視窗(透過呼叫[EnumProgram,](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)然後在每個程式上調用[EnumModule)。](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)

- 填充**附加到行程**清單(通過`IDebugProcess2::EnumPrograms`呼叫 ,然後呼叫每個[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)[介面上的查詢介面](/cpp/atl/queryinterface)以取得[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)介面)。

- 生成可以除錯過程中每個程式的 D 的 D 清單(使用[GetEngineInfo)。](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)

- 對每個程式應用編輯和繼續 (ENC) 更新(透過調用 IDebugProcess2:::枚舉程式,然後調用[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md))。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
