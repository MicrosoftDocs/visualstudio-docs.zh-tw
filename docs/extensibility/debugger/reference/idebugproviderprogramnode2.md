---
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b21b643c372cb5481868bc28496f273d4b6a5287
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041343"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
此介面中，封送處理程式相關的介面跨處理序界限。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 實作的相同物件上實作這個介面[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)以支援跨處理序界限的封送處理的介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugProgramNode2`介面，以取得此介面。 如果無法取得此介面，DE 不支援封送處理的介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|取得指定的介面，跨處理序界限。|  
  
## <a name="remarks"></a>備註  
 DE 執行不同的處理序空間中，從正在偵錯程式時，會實作這個介面： 例如，當 DE 執行 Visual Studio 處理序空間，而不是正在偵錯之程式的處理序空間中。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)