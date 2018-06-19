---
title: IDebugProcess3 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21c4dfffe02d2550bccf5b23f264ab8283524aa2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121088"
---
# <a name="idebugprocess3"></a>IDebugProcess3
此介面代表正在執行的程序，而且它的程式。 這個介面是用來取代中的數個方法[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。 它可控制程序中的所有程式。  
  
> [!NOTE]
>  [繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)， [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)，和[步驟](../../../extensibility/debugger/reference/idebugprogram2-step.md)方法已被取代，無法再使用。 使用上的對應方法`IDebugProcess3`改為介面。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 若要以群組方式管理程式自訂連接埠供應商被實作這個介面。 程式以群組進行管理，可以控制其執行，並建立一種語言的運算式評估工具。 連接埠提供者必須實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面稱為主要是由工作階段的偵錯管理員 (SDM) 才能與此程序所識別的程式群組互動。  
  
 呼叫[QueryInterface](/cpp/atl/queryinterface)上[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)，`IDebugProcess3`實作下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|會繼續執行，或是逐步執行處理程序。|  
|[執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|開始執行的處理序。|  
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|步驟會轉送一指示或在程序中的陳述式。|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|取得處理序已啟動的偵錯的原因。|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|設定主機的語言，如此偵錯引擎可以載入適當的運算式評估工具。|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|擷取目前針對此程序設定的語言。|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|此程序，停用編輯後繼續 (ENC)。<br /><br /> 自訂連接埠供應商不實作這個方法 (它應該會一律傳回`E_NOTIMPL`)。|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|取得這個處理程序 ENC 狀態。<br /><br /> 自訂連接埠供應商不實作這個方法 (它應該會一律傳回`E_NOTIMPL`)。|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|擷取可用的偵錯引擎的唯一識別碼的陣列。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)