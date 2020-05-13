---
title: IEnum調試錯誤斷點2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea841a095964b71e301e966bfd0a10c8f7c0c65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716879"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
此介面枚舉與掛起斷點關聯的錯誤斷點。

## <a name="syntax"></a>語法

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面作為其對斷點的支援的一部分。

## <a name="notes-for-callers"></a>通話備註
 Visual Studio 呼叫[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)以取得此介面,表示無法綁定的斷點清單,或[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)以取得此介面,表示未綁定的斷點清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugErrorBreakpoints2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|檢索枚舉序列中指定數量的錯誤斷點。|
|[跳](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|在枚舉序列中跳過指定數量的錯誤斷點。|
|[重設](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|獲取枚舉器中的錯誤斷點數。|

## <a name="remarks"></a>備註
 此介面包含[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面的清單,每個介面都描述了無法綁定的斷點以及為什麼無法綁定。 Visual Studio`IEnumDebugErrorBreakpoint2`使用該介面更新 IDE 中顯示的斷點。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
