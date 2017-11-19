---
title: "IDebugStackFrame2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2
helpviewer_keywords: IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d7c08cd7fc89e33ef9d505c9e32c23737ef7e84
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
此介面代表在特定執行緒的呼叫堆疊中的單一堆疊框架。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表堆疊框架。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)擷取[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面。 呼叫[下一步](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)擷取[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構，其中包含`IDebugStackFrame2`介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugStackFrame2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|取得此堆疊框架的程式碼內容。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|取得此堆疊框架的文件內容。|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|取得堆疊框架的名稱。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|取得堆疊框架的描述。|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|取得電腦相關的堆疊框架相關聯的實體位址範圍的表示。|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|取得評估內容執行堆疊框架和執行緒的目前內容中的運算式評估。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|取得與堆疊框架相關聯的語言。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|取得與堆疊框架關聯的屬性描述。|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|建立列舉值的堆疊框架屬性。|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|取得與堆疊框架關聯的執行緒。|  
  
## <a name="remarks"></a>備註  
 正在偵錯的程式已停止於中斷點 （使用者設定中斷點或例外狀況所造成） 時，才可取得此介面。 從這個介面，可取得運算式內容來評估運算式、 可傳回暫存器的清單，或可以取得並檢查呼叫堆疊。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)