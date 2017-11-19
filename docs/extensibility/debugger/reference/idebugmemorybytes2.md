---
title: "IDebugMemoryBytes2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryBytes2
helpviewer_keywords: IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80e60a6cfb31532c04963e0347fe95e415d32af4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
此介面代表位元組的記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表記憶體中的位元組。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)傳回這個介面可提供存取權的系統記憶體。 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)和[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)傳回這個介面可提供存取物件的位元組。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugMemoryBytes2`。  
  
|方法|說明|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|讀取在指定位置開始的位元組序列。|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|寫入`dwCount`開始的位元組`pStartContext`。|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|取得大小，以位元組為單位，表示此介面的記憶體。|  
  
## <a name="remarks"></a>備註  
 屬性， [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面代表陣列提供`IDebugMemoryBytes2`介面，以存取該陣列中的值。  
  
 Visual Studio**記憶體檢視**呼叫[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)擷取`IDebugMemoryBytes2`介面來存取系統記憶體。 取得存取位址由剖析為位址輸入記憶體檢視運算式，並評估剖析的運算式使用[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)取得`IDebugProperty2`介面。 呼叫[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)傳回[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)描述的記憶體位址。 此記憶體內容會接著傳遞給[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)和[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)