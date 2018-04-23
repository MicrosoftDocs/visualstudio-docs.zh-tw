---
title: IDebugProcessQueryProperties |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac071afd9f9ce7d45a05408aeec32117776832f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
這個介面是由延伸模組介面[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)實作者。 它可讓實作器，以取得有關偵錯的處理序環境。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 實作這個介面來取得有關偵錯的處理序的執行環境。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProcessQueryProperties`。  
  
|方法|描述|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|屬性值的查詢。|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|屬性值的查詢。|  
  
## <a name="remarks"></a>備註  
 很少實作這個介面。  
  
## <a name="requirements"></a>需求  
 標頭： Portpriv.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)