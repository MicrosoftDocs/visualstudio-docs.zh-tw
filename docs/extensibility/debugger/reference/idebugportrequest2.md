---
title: IDebugPortRequest2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a05f84d685ac33203461dfc1b0f515cb45f67c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876925"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
這個介面會描述連接埠。 若要將連接埠新增至連接埠提供者會使用這個描述。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 Visual Studio 通常會實作這個介面，在過程中從連接埠提供者取得偵錯連接埠。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面傳入[下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)建立偵錯連接埠。 呼叫[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)傳回這個介面，代表用來在一開始建立連接埠的要求。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPortRequest2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|取得要建立的連接埠的名稱。|  
  
## <a name="remarks"></a>備註  
 偵錯引擎通常不會使用連接埠提供者互動，而且必須沒有使用此介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)