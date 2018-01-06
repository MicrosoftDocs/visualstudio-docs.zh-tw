---
title: "IEnumDebugPropertyInfo2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPropertyInfo2
helpviewer_keywords: IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 578418c1afa831120cf77fd5a1da48d84126ec8f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
這個介面會列舉[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表特定屬性的資訊。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)取得此介面代表特定屬性的子系。 呼叫[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)取得此介面代表特定堆疊框架的內容。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugPropertyInfo2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|擷取指定的數目的[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)列舉順序中的結構。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|略過指定的數目的[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)列舉順序中的結構。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|列舉序列重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態相同。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|取得數目[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)中查看的列舉值的結構。|  
  
## <a name="remarks"></a>備註  
 一般情況下，屬性是階層的名稱、 值、 位址和型別，可以包含的資訊，以及適用於相關聯的屬性物件或堆疊框架的任何其他資訊。 請參閱[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)如需詳細資訊。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)