---
title: IDebugErrorBreakpoint2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9895caedebfba637eb47198c408e973e6609fcc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183951"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面代表錯誤或警告中斷點，例如不正確位置、不正確運算式，或暫止中斷點尚未系結 (程式碼尚未載入，因此) 的原因。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugErrorBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 偵錯工具引擎會在其支援中斷點的過程中，執行這個介面。 這個介面是用來報告系結中斷點的問題。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 對 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) 的呼叫會取得這個介面。 這個介面也可以 (為[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)或[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)呼叫所) 的[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)介面所代表之清單的一部分傳回。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugErrorBreakpoint2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|取得造成錯誤的暫止中斷點。|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|取得描述錯誤的中斷點錯誤解決方法。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [下](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
