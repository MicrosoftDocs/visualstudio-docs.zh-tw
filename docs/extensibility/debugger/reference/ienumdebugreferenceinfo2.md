---
title: IEnumDebug參考資訊2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6132235a7e4789c7d9efe5bae9d7fd531112dab4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715272"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
此介面枚舉[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。

## <a name="syntax"></a>語法

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面,作為其對記憶體中物件的引用的支援的一部分。 僅當支援引用時,才能實現此介面。

## <a name="notes-for-callers"></a>通話備註
 Visual Studio 調用[Enum 兒童](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugReferenceInfo2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|檢索枚舉序列中指定數量的[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。|
|[跳](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|跳過枚舉序列中指定數量的[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。|
|[重設](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|獲取枚舉器中[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構的數量。|

## <a name="remarks"></a>備註
 引用本質上是一個類型和位址,而屬性是名稱、類型和位址。 只要引用的物件存在於記憶體中,引用就保持不變。 有關詳細資訊[,請參閱 IDebug 參考 2。](../../../extensibility/debugger/reference/idebugreference2.md)

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
