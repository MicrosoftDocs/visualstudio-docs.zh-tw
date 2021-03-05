---
description: 此介面會通知接聽程式 (通常是會話 debug manager [SDM] 或偵錯工具) 進程的進程和程式建立，並在特定埠上進行銷毀。
title: IDebugPortEvents2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 50dadee6ac2e1d1a441796aac7ca49614b84bcdf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169466"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
此介面會通知接聽程式 (通常是會話 debug manager [SDM] 或偵錯工具) 進程的進程和程式建立，並在特定埠上進行銷毀。 這項資訊可用來即時查看在埠上執行的進程和程式。

## <a name="syntax"></a>Syntax

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Visual Studio 通常會執行這個介面，以接收有關程式建立和終結的通知。 偵錯工具引擎也可以執行此介面來接聽這類埠事件。

## <a name="notes-for-callers"></a>呼叫者注意事項
 所有 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 介面都可以針對介面進行查詢 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 。 然後， <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> `IDebugPortEvents2` 會在介面中呼叫的方法 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> ，以取得 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 介面。 最後， <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> 會呼叫介面中的方法， <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 透過 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md) 方法傳送事件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugPortEvents2` 。

|方法|描述|
|------------|-----------------|
|[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)|傳送描述在埠上建立和終結進程和程式的事件。|

## <a name="remarks"></a>備註
 `IDebugPortEvents2` SDM 也會使用，來將在已進行調試的進程中執行的程式進行偵錯工具。

 埠事件會由這個介面傳遞給 SDM。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
