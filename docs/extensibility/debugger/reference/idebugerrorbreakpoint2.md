---
title: IDebugErrorBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c557a155c68b3a45e2b96aceee8ddcfcaa1d82e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874636"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
這個介面會表示錯誤或警告中斷點，例如無效的位置、 無效的運算式或為何暫止中斷點具有未繫結 （程式碼不會載入尚未等等） 的原因。

## <a name="syntax"></a>語法

```
IDebugErrorBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎會實作這個介面做為其支援中斷點的一部分。 這個介面用來報告繫結中斷點的問題。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)取得這個介面。 此介面也可能會傳回 (表示清單的一部分[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)介面) 的呼叫所[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)或[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugErrorBreakpoint2`。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|取得造成錯誤的暫止中斷點。|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|取得描述錯誤的中斷點錯誤解決方式。|

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)