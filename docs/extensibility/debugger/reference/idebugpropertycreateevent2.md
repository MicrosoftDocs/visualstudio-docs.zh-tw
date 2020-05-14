---
title: IDebug屬性建立事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720925"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
此介面由除錯引擎 (DE) 傳送到工作階段除錯管理員 (SDM) 時,它建立與特定文件關聯的屬性。

## <a name="syntax"></a>語法

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以報告已創建屬性。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現。 SDM 使用[查詢介面](/cpp/atl/queryinterface)訪問`IDebugEvent2`介面。 如果 DE 創建了與已載入或創建的文稿關聯的屬性,並且該文本需要顯示在 IDE 中,則實現此介面。

## <a name="notes-for-callers"></a>通話備註
 DE 創建並發送此事件物件以報告已創建屬性。 該事件使用 SDM 在附加到正在調試的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數進行發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示了`IDebugPropertyCreateEvent2`介面的方法。

|方法|描述|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|獲取新屬性。|

## <a name="remarks"></a>備註
 如果屬性具有與其關聯的特定文檔或腳本,DE 可以將此事件發送到 SDM,以便使用文檔的名稱更新**文稿文件**視窗。 SDM 將使用`guidDocument`參數 呼叫[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)以`VARIANT`檢索包含[I 未知指標的](/cpp/atl/iunknown)指標。 SDM 將在此指標上調用[QueryInterface](/cpp/atl/queryinterface)以檢索用於更新**文稿文件**視窗的[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
