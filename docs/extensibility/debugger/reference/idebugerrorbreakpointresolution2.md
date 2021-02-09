---
title: IDebugErrorBreakpointResolution2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2
helpviewer_keywords:
- IDebugErrorBreakpointResolution2
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1581e9f00e4a2dcb0a7bdab67cfe601b1c9dd05f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888377"
---
# <a name="idebugerrorbreakpointresolution2"></a>IDebugErrorBreakpointResolution2
此介面代表中斷點錯誤的解決方式。

## <a name="syntax"></a>Syntax

```
IDebugErrorBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 偵錯工具引擎會在其支援中斷點的過程中，執行這個介面。 這個介面是用來報告中斷點無法系結的位置。

## <a name="notes-for-callers"></a>呼叫者注意事項
 對 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 的呼叫會傳回這個介面，以提供中斷點無法系結的相關資訊。 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)方法會取得[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugErrorBreakpointResolution2` 。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|取得中斷點型別。|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|取得中斷點解析資訊。|

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
