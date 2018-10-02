---
title: IDebugDocumentTextEvents2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95eae8da7779a23e9bf285eff2f637fbcd4633e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491352"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugDocumentTextEvents2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumenttextevents2)。  
  
此介面用來偵錯引擎所提供的來源文件變更的相關通知 Visual Studio。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 DE 會實作這個介面，以支援的原始程式碼進行變更。 通常會實作這個介面上相同的物件會實作[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 取得這個介面，透過呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>方法。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面取自呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>方法。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面由呼叫[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)方法[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugDocumentTextEvents2`。  
  
|方法|描述|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|表示已終結整份文件。|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|已插入文件插入文字會告知偵錯封裝。|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|告知偵錯封裝文字具有從文件中移除。|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|文件中，已被取代的文字會告知偵錯封裝。|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|文件中，已更新文字屬性會告知偵錯封裝。|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|通知事件的接收者，已更新的文件屬性。|  
  
## <a name="remarks"></a>備註  
 僅提供自己的文件的偵錯引擎會利用`IDebugDocumentTextEvent2`介面。 這個範例是指令碼的偵錯引擎。 解譯指令碼的過程中新的原始程式碼可能會產生不存在的任何磁碟檔中，只有知道 DE。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

