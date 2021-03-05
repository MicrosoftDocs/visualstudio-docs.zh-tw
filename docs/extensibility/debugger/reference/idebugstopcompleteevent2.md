---
description: 當程式停止時，debug engine (DE) 可以將這個選擇性事件傳送至會話 debug manager (SDM) 。
title: IDebugStopCompleteEvent2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d96aa335c8951b9dfc80517bf797338cd590b48
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159740"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

當程式停止時，debug engine (DE) 可以將這個選擇性事件傳送至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項

此介面是在 Visual Studio 2005 中引進。 先前的版本不支援非同步停止。

- 多進程或多程式案例中的 SDM 會呼叫[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 。 當某個程式將停止事件傳送至 SDM 時，SDM 也會要求其他程式停止。

停止是用來以非同步方式通知 SDM 程式已停止。 通知 SDM 對解譯器的偵測引擎很有用，在這種情況下，在程式碼的程式碼中有時不會執行任何程式碼，所以無法同步完成 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 。 如果「debug engine」想要採用此非同步通知，它必須 `S_ASYNC_STOP` 從「 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)」回來。

## <a name="requirements"></a>規格需求

標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll
