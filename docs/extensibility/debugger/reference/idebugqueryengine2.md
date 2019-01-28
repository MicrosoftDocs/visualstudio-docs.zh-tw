---
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b32464084a209aa7d6f41ffaa837d2f377b9720a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984388"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
此介面可讓偵錯管理員 (SDM) 擷取介面，代表偵錯引擎 (DE) 的工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 DE 實作此介面上實作的最常見的 DE 介面的物件 (例如[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)， [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)，並[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) 中若要允許存取的順序[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) DE 本身的介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](/cpp/atl/queryinterface)典型的 DE 介面，以取得此介面上。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugQueryEngine2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|取得自訂的偵錯引擎 (DE) 介面。|  
  
## <a name="remarks"></a>備註  
 通常會實作這個介面中實作的物件[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面以支援因果順序逐步執行函式，也就是當偵錯工具會跳離函式若要執行的下一個函式可能不是在堆疊上的前一個函式，但另一個執行緒中的函式完全。 如需 「 原因 」 的定義，請參閱 < [Visual Studio 偵錯工具字彙](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)