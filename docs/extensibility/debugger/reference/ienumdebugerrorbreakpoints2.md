---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d204b29b46e257d4ca0b8c4102c3a64e9e78adf1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317234"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
此介面列舉暫止中斷點相關聯的錯誤中斷點。

## <a name="syntax"></a>語法

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面做為其支援中斷點的一部分。

## <a name="notes-for-callers"></a>呼叫端資訊
 Visual Studio 呼叫[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)若要取得此介面，表示清單中的中斷點無法繫結，或[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)來取得這個介面，表示中斷點的清單未繫結。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugErrorBreakpoints2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|擷取指定的數目的列舉型別序列中的錯誤中斷點。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|略過指定的數目的列舉型別序列中的錯誤中斷點。|
|[Reset](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|將列舉型別序列重設到開頭。|
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|取得列舉值中的錯誤中斷點的數目。|

## <a name="remarks"></a>備註
 這個介面會保留一份[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面，其中每個描述，可能不會繫結，以及為何它可能不會繫結的中斷點。 Visual Studio 會使用`IEnumDebugErrorBreakpoint2`介面，以更新顯示在 IDE 中的中斷點。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)