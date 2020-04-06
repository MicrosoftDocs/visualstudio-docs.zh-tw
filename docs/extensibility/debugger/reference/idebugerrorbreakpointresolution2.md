---
title: IDebug錯誤斷點決議2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2
helpviewer_keywords:
- IDebugErrorBreakpointResolution2
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d922259034d4e99c43fc06cfef8228b013fb180f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730015"
---
# <a name="idebugerrorbreakpointresolution2"></a>IDebugErrorBreakpointResolution2
此介面表示斷點錯誤的解決方法。

## <a name="syntax"></a>語法

```
IDebugErrorBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 調試引擎實現此介面作為其對斷點的支援的一部分。 此介面用於報告斷點無法綁定的位置。

## <a name="notes-for-callers"></a>通話備註
 對[GetBreakpoint 解析的](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)調用將返回此介面,以提供有關斷點無法綁定的位置的資訊。 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)方法獲取[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugErrorBreakpointResolution2`。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|獲取斷點類型。|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|獲取斷點解析度資訊。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
