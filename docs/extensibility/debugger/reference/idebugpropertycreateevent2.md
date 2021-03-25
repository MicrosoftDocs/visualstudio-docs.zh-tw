---
description: 此介面是由偵錯工具在建立與特定檔相關聯的屬性時， (DE) 至會話 debug manager (SDM) 所傳送。
title: IDebugPropertyCreateEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6197420428bf07cecf2bfe891e06ddb7a830ea30
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083878"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
此介面是由偵錯工具在建立與特定檔相關聯的屬性時， (DE) 至會話 debug manager (SDM) 所傳送。

## <a name="syntax"></a>Syntax

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行此介面來報告已建立的屬性。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。 如果 DE 已建立與已載入或建立的腳本相關聯的屬性，而且該腳本需要出現在 IDE 中，就會執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 「取消」會建立並傳送此事件物件，以報告已建立的屬性。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示介面的方法 `IDebugPropertyCreateEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|取得新的屬性。|

## <a name="remarks"></a>備註
 如果屬性具有與其相關聯的特定檔或腳本，則會將此事件傳送至 SDM，以便使用檔的名稱來更新 [ **指令檔** ] 視窗。 SDM 會以引數呼叫 [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) ， `guidDocument` 以取出 `VARIANT` 包含 [IUnknown](/cpp/atl/iunknown) 指標的。 SDM 會呼叫這個指標上的 [QueryInterface](/cpp/atl/queryinterface) ，以抓取用來更新 **指令檔** 視窗的 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
