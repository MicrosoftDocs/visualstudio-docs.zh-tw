---
title: "IDebugDocumentTextEvents2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentTextEvents2
helpviewer_keywords: IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb9e284435cdf8a5905e068b0044cd118a1621c9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
這個介面用來偵錯引擎所提供的來源文件變更的相關通知 Visual Studio。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面來支援變更原始碼。 通常會實作這個介面會實作在相同物件上[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]取得此介面，透過呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>方法。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面取自呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>方法。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面透過呼叫[QueryInterface](/cpp/atl/queryinterface)方法[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugDocumentTextEvents2`。  
  
|方法|描述|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|表示已終結整份文件。|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|已加入文件中插入文字會告知偵錯封裝。|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|告知偵錯封裝文字具有從文件中移除。|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|文件中，已取代的文字會告知偵錯封裝。|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|告知偵錯封裝中的文件，已更新文字屬性。|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|通知事件的接收者，文件屬性已更新。|  
  
## <a name="remarks"></a>備註  
 僅提供自己的文件的偵錯引擎會利用`IDebugDocumentTextEvent2`介面。 這個範例是指令碼的偵錯引擎。 在解譯指令碼，新的原始程式碼可以產生，但不存在於任何磁碟檔案中只有知道 DE。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)