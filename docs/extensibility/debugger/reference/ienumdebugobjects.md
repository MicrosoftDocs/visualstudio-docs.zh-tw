---
title: "IEnumDebugObjects |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugObjects
helpviewer_keywords: IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c8f62f4a153ac5c5966721578313245fc02f7d04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此介面代表實作物件的集合[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 運算式評估工具會實作這個介面可提供實作的物件集的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面。 請注意，這不是標準的 COM 列舉的緣故[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)方法。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|擷取下的一組[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)列舉中的物件。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|略過指定的數目的項目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|將列舉重設第一個項目。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|擷取一份目前的列舉。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|擷取列舉中的項目數目。|  
  
## <a name="remarks"></a>備註  
 這個介面可讓偵錯引擎来列舉一組的陣列中的物件。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)