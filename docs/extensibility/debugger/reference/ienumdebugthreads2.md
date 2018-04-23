---
title: IEnumDebugThreads2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3405a8ab52591e79f5a865016b68c69c61e6cf8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
此 interfac 列舉在目前的偵錯工作階段中執行的執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表在程式中執行緒的清單。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)取得此介面代表所有處理序中執行的程式中的所有執行緒的清單。 呼叫[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)取得此介面代表在程式中執行之執行緒的清單。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugThreads2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|擷取指定的列舉順序中的執行緒數目。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|略過指定的列舉順序中的執行緒數目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|列舉序列重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|建立列舉值，包含目前的列舉型別狀態相同。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|取得列舉值中的執行緒數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 通常會取得此介面，以便更新**執行緒**視窗以及取得第一個執行緒的清單中，若要呼叫[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)，[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)，和[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)