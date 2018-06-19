---
title: IDebugPortEvents2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: af2652bd18ff5d371389e8d3a7d3ab4c477eaa34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120032"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
這個介面通知程序和程式建立和解構的特定連接埠上接聽的程式 （通常是工作階段偵錯管理員 [SDM] 或偵錯引擎）。 這項資訊可以用來呈現的程序和程式的連接埠上執行的即時檢視。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 Visual Studio 通常會實作這個介面來接收通知程式建立和解構。 偵錯引擎也可以實作這個介面來接聽此類連接埠事件。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 所有[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面可以查詢<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面。 然後在<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A>方法`IDebugPortEvents2`中呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面，以取得<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面。 最後，<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>方法中的<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面稱為透過傳送事件[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPortEvents2`。  
  
|方法|描述|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|傳送說明建立和解構的處理序和程式的連接埠上的事件。|  
  
## <a name="remarks"></a>備註  
 `IDebugPortEvents2` 也會使用 SDM 偵錯已經在偵錯處理序中執行的程式。  
  
 這個介面會將連接埠事件給 SDM。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)