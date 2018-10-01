---
title: IDebugPortEvents2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3eb6208d815e4951bd916d014cddfdda34a8e589
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490517"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugPortEvents2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportevents2)。  
  
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
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

