---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33272f87ae30832588a998ebea2fc46e9adaae50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984232"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

偵錯引擎 (DE) 在程式停止時，可以傳送這個選擇性事件工作階段的偵錯管理員 (SDM)。

## <a name="syntax"></a>語法

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註

使用 Visual Studio 2005 中引進這個介面。 先前的版本不支援非同步停止。

[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)SDM 多處理序或多重程式案例中會呼叫。 當某個程式停止將事件傳送到 SDM 時，SDM 會要求太停止其他程式。

停駐點用來以非同步方式通知程式已停止在 SDM。 通知 SDM 適合用來解譯器偵錯引擎，有時也沒有任何程式碼執行內偵錯程式，因此[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)未以同步方式完成。 如果偵錯引擎想要運用此非同步通知時，它必須傳回`S_ASYNC_STOP`從[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)。

## <a name="requirements"></a>需求

標頭： msdbg.h

命名空間:Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll