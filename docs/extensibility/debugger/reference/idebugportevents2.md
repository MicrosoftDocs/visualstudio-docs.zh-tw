---
title: IDebugPortEvents2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725183"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
此介面通知偵聽器(通常是會話調試管理器 [SDM] 或調試引擎)特定埠上的進程和程式創建和銷毀。 此資訊可用於顯示在埠上運行的進程和程式的即時檢視。

## <a name="syntax"></a>語法

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 Visual Studio 通常實現此介面來接收有關程式創建和銷毀的通知。 調試引擎還可以實現此介面來偵聽此類埠事件。

## <a name="notes-for-callers"></a>通話備註
 可以查詢所有[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 在介面中<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>呼叫`IDebugPortEvents2`方法以取得介面<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> 最後,<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>調用介面<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>中 的方法通過[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)方法發送事件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugPortEvents2`。

|方法|描述|
|------------|-----------------|
|[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)|發送描述埠上進程和程式的創建和銷毀的事件。|

## <a name="remarks"></a>備註
 `IDebugPortEvents2`SDM 還用於調試在已調試的進程中運行的程式。

 埠事件通過此介面傳遞到 SDM。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
