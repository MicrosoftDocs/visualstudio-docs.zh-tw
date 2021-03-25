---
description: 偵錯工具引擎會使用這個介面 (DE) 將訊息傳送至需要使用者回應的 Visual Studio。
title: IDebugMessageEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5593e822b974ddb7c666f622192e3e4630b7222
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058426"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
偵錯工具引擎會使用這個介面 (DE) 將訊息傳送至需要使用者回應的 Visual Studio。

## <a name="syntax"></a>Syntax

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面，將訊息傳送至需要使用者回應的 Visual Studio。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。

 這個介面的執行必須將 Visual Studio 的 [responsemanager](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) 呼叫傳達給 DE。 例如，您可以使用張貼至解除郵件處理執行緒的訊息來完成這件工作，或者執行這個介面的物件可以保留對 DE 的參考，然後再呼叫傳回的回應 `IDebugMessageEvent2::SetResponse` 。

## <a name="notes-for-callers"></a>呼叫者注意事項
 「取消」會建立並傳送此事件物件，向需要回應的使用者顯示訊息。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugMessageEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|取得要顯示的訊息。|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|從訊息方塊設定回應（如果有的話）。|

## <a name="remarks"></a>備註
 如果需要特定訊息的使用者特定回應，則 DE 將會使用此介面。 例如，如果在嘗試遠端附加至程式之後，取消了「拒絕存取」訊息，則會將此特定訊息傳送至 `IDebugMessageEvent2` 具有訊息方塊樣式的事件中 Visual Studio `MB_RETRYCANCEL` 。 這可讓使用者重試或取消附加作業。

 DE 會依照 Win32 函數的慣例來指定如何處理此訊息 `MessageBox` (如需詳細資料，請參閱 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)) 。

 使用 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) 介面，將訊息傳送至不需要使用者回應的 Visual Studio。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
