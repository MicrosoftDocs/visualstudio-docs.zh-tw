---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49224ad0018286fffd365857364bf1b37300788f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918842"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
此介面由偵錯引擎 (DE) 用於將訊息傳送至 Visual Studio 需要來自使用者的回應。

## <a name="syntax"></a>語法

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 DE 會實作這個介面來傳送訊息至 Visual Studio 所需的使用者回應。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上。 使用 SDM [QueryInterface](/cpp/atl/queryinterface)若要存取`IDebugEvent2`介面。

 這個介面的實作必須與其進行通訊的 Visual Studio 呼叫[Responsemanager](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) DE 到。 比方說，這可以使用訊息，張貼至 DE 的訊息處理執行緒，或實作這個介面的物件可以保存 DE 的參考，並與回應傳遞至回撥 DE `IDebugMessageEvent2::SetResponse`。

## <a name="notes-for-callers"></a>呼叫端資訊
 DE 建立，並傳送這個事件物件需要回應對使用者顯示一則訊息。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)附加至正在進行偵錯程式時，會將 SDM 所提供的回呼函式。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugMessageEvent2`。

|方法|描述|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|取得要顯示的訊息。|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|如果有的話，從訊息方塊，請設定所做出的回應。|

## <a name="remarks"></a>備註
 預設會使用此介面，如果需要使用者的特定回應特定訊息。 比方說，如果 DE 取得 「 拒絕存取 」 訊息，嘗試從遠端將其附加至程式之後，DE 會傳送此特定訊息中的 Visual studio`IDebugMessageEvent2`事件的訊息方塊樣式`MB_RETRYCANCEL`。 這可讓使用者重試一次，或取消在附加作業。

 DE 指定由下列的 Win32 函式的慣例來處理此訊息有何`MessageBox`(請參閱 < [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)如需詳細資訊)。

 使用[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)介面將訊息傳送至 Visual Studio 不需要使用者回應。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)