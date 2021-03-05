---
description: 此介面是用來通知 Visual Studio 有關由 debug 引擎所提供的來源文件變更。
title: IDebugDocumentTextEvents2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bcbe6e44923172c3eac4da605848e972216837cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154180"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
此介面是用來通知 Visual Studio 有關由 debug 引擎所提供的來源文件變更。

## <a name="syntax"></a>Syntax

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面，以支援對原始程式碼進行變更。 這個介面通常會在執行 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 介面的相同物件上執行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 透過呼叫方法來取得這個介面 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> 。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面是從呼叫方法所取得 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> 。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面是藉由在[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面上呼叫[QueryInterface](/cpp/atl/queryinterface)方法來取得。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugDocumentTextEvents2` 。

|方法|描述|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|表示整份檔已損毀。|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|通知偵錯工具封裝文字已插入檔中。|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|通知偵錯工具封裝文字已從檔中移除。|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|通知偵錯工具封裝檔中的文字已被取代。|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|通知偵錯工具封裝檔中的 text 屬性已更新。|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|通知接收者已更新檔案屬性的事件。|

## <a name="remarks"></a>備註
 只有提供專屬檔的偵錯工具引擎會利用 `IDebugDocumentTextEvent2` 介面。 其中一個範例就是腳本處理的偵錯工具引擎。 在解讀腳本的過程中，可能會產生不存在於任何磁片檔案中的新原始程式碼，而且只有 DE 才知道。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
