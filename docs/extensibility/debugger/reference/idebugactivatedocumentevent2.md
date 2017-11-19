---
title: "IDebugActivateDocumentEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugActivateDocumentEvent2
helpviewer_keywords: IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f21648f9b019fbb765290d969b1a6c68fe5ce2f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
偵錯引擎 (DE) 會使用此介面來要求要載入的文件。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 需要開啟原始程式檔時，DE 會實作這個介面。 只能由偵錯引擎會處理或屬於指令碼解譯器會實作這個介面。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件上 (SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 建立裝置和需要具有開啟原始程式檔時，會傳送此事件的物件。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugActivateDocumentEvent2`。  
  
|方法|說明|  
|-------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|取得要啟動的文件。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|取得描述文件中的位置的文件內容。|  
  
## <a name="remarks"></a>備註  
 此介面用的一般案例是剖析錯誤發生在 HTML 網頁上的指令碼中，如果指令碼 DE 會傳送這個介面來 SDM 如此可以顯示文件剖析錯誤。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)