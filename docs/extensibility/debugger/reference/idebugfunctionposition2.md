---
title: "IDebugFunctionPosition2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionPosition2
helpviewer_keywords: IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ae7a0dd442d8a48d6c69ecfd51b2fc17a2eb2fe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
此介面代表來源文件中的函式的抽象位置。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作此介面代表來源文件內的函式的位置。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面提供作為一部分[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)等位 (具體而言， [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)結構)，接著是一部分[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構，用來建立暫止中斷點。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugFunctionPosition2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|取得這個位置就是相對於函式的名稱。|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|取得從函式開頭位移。|  
  
## <a name="remarks"></a>備註  
 此介面所表示的位置是以文字為基礎，特別是， [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)