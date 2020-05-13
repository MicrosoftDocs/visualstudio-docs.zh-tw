---
title: IDebug文檔文字事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731361"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
此介面用於通知 Visual Studio 有關調試引擎提供的源文件的更改。

## <a name="syntax"></a>語法

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以支援對原始碼進行更改。 此介面通常實現於實現[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面的同一物件上。

## <a name="notes-for-callers"></a>通話備註
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]通過調用<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>方法獲取此介面。 介面<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>是從<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>對 方法的調用中獲得的。 介面<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>是通過在[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面上調用[查詢介面](/cpp/atl/queryinterface)方法獲得的。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugDocumentTextEvents2`。

|方法|描述|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|指示整個文件已銷毀。|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|通知調試包文本已插入到文檔中。|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|通知除錯包文本已從文件中刪除。|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|通知調試包文件中已替換文本。|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|通知調試包文件中的文本屬性已更新。|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|通知接收方事件文件屬性已更新。|

## <a name="remarks"></a>備註
 只有除錯引擎來提供自己的文件才能利用介面`IDebugDocumentTextEvent2`。 例如腳本調試引擎。 在解釋文稿的過程中,可以生成任何磁碟檔中不存在且僅 DE 知道的新原始程式碼。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
