---
description: 此介面是由偵錯工具引擎傳送 (DE) 至會話 debug manager (SDM) 以輸出字串。
title: IDebugOutputStringEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4576914ada9a575569ce09c120dbbd9bc11fdfa9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084645"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
此介面是由偵錯工具引擎傳送 (DE) 至會話 debug manager (SDM) 以輸出字串。

## <a name="syntax"></a>Syntax

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面，以將字串傳送至 IDE 的 **輸出** 視窗。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 「取消」會建立並傳送此事件物件，以將字串傳送至 [ **輸出** ] 視窗。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugOutputStringEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|取得可顯示的訊息。|

## <a name="remarks"></a>備註
 例如，在非受控程式碼中，所要輸出的字串會在正在進行偵錯工具傳送字串至 Win32 函數時產生 `OutputDebugString` 。 這個字串會由 DE 攔截，並傳送至 SDM 作為 `IDebugOutputStringEvent2` 事件。

 使用 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) 傳送需要使用者回應的訊息。

 使用 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) 傳送不需要回應的錯誤訊息。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
