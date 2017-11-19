---
title: "IDebugProperty3 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3
helpviewer_keywords: IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 091ebddc0c3424bdbf8126257fe56e6959bc28c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty3"></a>IDebugProperty3
這個介面提供的支援：  
  
-   擷取與屬性相關聯的任意長度字串。  
  
-   關聯屬性的唯一識別碼。  
  
-   擷取屬性的自訂檢視器的清單。  
  
-   設定屬性的值，能夠報告任何產生的錯誤  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 實作的相同物件上實作此介面[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)長字串、 屬性識別碼和自訂檢視器提供支援。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugProperty2`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自`IDebugProperty2`、`IDebugProperty3`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|傳回與屬性相關聯的字串長度。|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|使用者提供的緩衝區中傳回的字串。|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|建立這個屬性的唯一識別碼。|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|終結此屬性的唯一識別碼。|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|傳回這個屬性可以使用檢視的自訂檢視器的數目。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|傳回這個屬性可以使用檢視的自訂檢視器清單。|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|設定這個屬性，傳回錯誤訊息，如果任何項目發生錯誤的值。|  
  
## <a name="remarks"></a>備註  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)慣用的方法為工作階段的偵錯管理員 (SDM) 來設定屬性的值。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)