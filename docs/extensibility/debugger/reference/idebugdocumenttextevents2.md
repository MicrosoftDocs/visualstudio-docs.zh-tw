---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e24568d307db694d30a5e87630f47f764a036427
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921280"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
此介面用來偵錯引擎所提供的來源文件變更的相關通知 Visual Studio。

## <a name="syntax"></a>語法

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 DE 會實作這個介面，以支援的原始程式碼進行變更。 通常會實作這個介面上相同的物件會實作[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。

## <a name="notes-for-callers"></a>呼叫端資訊
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 取得這個介面，透過呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>方法。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面取自呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>方法。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面由呼叫[QueryInterface](/cpp/atl/queryinterface)方法[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。

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

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)