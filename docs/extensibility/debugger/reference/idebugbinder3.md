---
title: IDebugBinder3 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 43465f919806f16154b8f3328aad7496c83ec235
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會提供存取型別、 別名和自訂視覺化檢視服務。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎實作這個介面來支援別名、 自訂視覺化檢視服務和物件類型資訊的存取權。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面取得此介面使用[QueryInterface](/cpp/atl/queryinterface)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了所提供的方法[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面，這個介面會實作下列：  
  
|方法|描述|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|擷取記憶體物件，代表此物件所繫結的記憶體。|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|擷取這個物件 （如果有的話），與相關聯的例外狀況|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|擷取指定其名稱、 別名|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|擷取所有的別名，對此物件的陣列|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|取得與這個物件相關聯的引數類型的數目|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|擷取這個物件相關聯的引數類型的清單|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|取得要視覺化檢視服務時介面|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|將記憶體內容的物件位置或 64 位元記憶體位址。|  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)