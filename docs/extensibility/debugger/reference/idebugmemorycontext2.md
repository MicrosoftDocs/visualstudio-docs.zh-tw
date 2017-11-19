---
title: "IDebugMemoryContext2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryContext2
helpviewer_keywords: IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d0f631d1cb41a0882dcf4d67754df24e6e83f23
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
此介面代表執行偵錯程式的電腦的位址空間中的位置。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表記憶體中的位址。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)或[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)傳回此介面。 此外，呼叫[新增](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)和[Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)套用適當的算術運算後傳回此介面的新複本。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugMemoryContext2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|取得此內容可顯示使用者的名稱。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|取得描述此內容的資訊。|  
|[[新增]](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|將指定的值加入至目前內容的位址，才能建立新的內容。|  
|[差集](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|減去指定的值，從目前內容的位址，才能建立新的內容。|  
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|比較兩個內容的方式所指定比較旗標。|  
  
## <a name="remarks"></a>備註  
 Visual Studio**記憶體**視窗呼叫[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)取得`IDebugMemoryContext2`介面，其中包含所用的記憶體位址的評估的運算式。 此內容接著會傳遞給[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)和[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)來指定要讀取或寫入的位址。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)