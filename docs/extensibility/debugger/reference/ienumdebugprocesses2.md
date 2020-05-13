---
title: IEnum調試過程2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b9fe0e96ade081e8da11b5e1c06c5b45279b10b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715751"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
此介面枚舉在調試埠上運行的進程。

## <a name="syntax"></a>語法

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 自定義埠供應商實現此介面以提供在埠上運行的進程的清單。

## <a name="notes-for-callers"></a>通話備註
 可視化工作室調用[Enum 進程](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugProcesses2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|檢索枚舉序列中指定數量的進程。|
|[跳](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|在枚舉序列中跳過指定數量的進程。|
|[重設](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|獲取枚舉器中的進程數。|

## <a name="remarks"></a>備註
 Visual Studio 使用此介面填充 **「進程」** 視窗。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
