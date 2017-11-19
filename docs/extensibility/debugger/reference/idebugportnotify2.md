---
title: "IDebugPortNotify2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortNotify2
helpviewer_keywords: IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9aec1465334a4399136d47c29faa8cccbb99c3a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
這個介面會註冊或取消登錄與連接埠執行才能進行偵錯的程式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 自訂連接埠供應商實作這個介面來支援新增和移除程式，從連接埠。 它通常會實作在相同物件上實作[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugPort2`介面會傳回此介面。 此外，若要呼叫[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)傳回此介面。 偵錯引擎可以為參數，以查看此介面[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPortNotify2`。  
  
|方法|說明|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|註冊可偵錯的程式與連接埠執行。|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|取消登錄從連接埠執行才能進行偵錯的程式。|  
  
## <a name="remarks"></a>備註  
 除非偵錯連接埠才有辦法知道程式會載入或卸載時，自訂連接埠供應商必須實作這個介面。 所有透過特定通訊埠偵錯已載入的程式會追蹤使用此介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)