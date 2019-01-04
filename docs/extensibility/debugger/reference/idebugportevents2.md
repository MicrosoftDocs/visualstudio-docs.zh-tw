---
title: IDebugPortEvents2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9701fe592e7e357b5f1a89d5bef884d4dbf1ce4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931125"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
這個介面會通知程序和程式的建立和解構的特定連接埠上接聽的程式 （通常是工作階段偵錯管理員 [SDM] 或偵錯引擎）。 這項資訊可用來呈現的程序和連接埠上執行程式的即時檢視。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 Visual Studio 通常會實作這個介面來接收通知程式建立和解構。 偵錯引擎也可以實作這個介面來接聽此連接埠事件。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 所有[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)可以查詢介面<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面。 然後<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A>方法`IDebugPortEvents2`中稱為<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面，以取得<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面。 最後，<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>方法中的<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面會呼叫來傳送事件通過[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPortEvents2`。  
  
|方法|描述|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|會傳送描述的建立和解構的處理序和程式的連接埠上的事件。|  
  
## <a name="remarks"></a>備註  
 `IDebugPortEvents2` 也會使用 SDM 偵錯已經在偵錯的處理序中執行的程式。  
  
 連接埠事件會傳遞至 SDM，此介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)