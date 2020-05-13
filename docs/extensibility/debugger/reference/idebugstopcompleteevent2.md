---
title: IDebugStop完成事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719452"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

當程式停止時,除錯引擎 (DE) 可以將此可選事件發送到工作階段調試管理員 (SDM)。

## <a name="syntax"></a>語法

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明

此介面是使用 Visual Studio 2005 引入的。 以前的版本不支援非同步停止。

- 在多進程或多程式方案中,SDM 調用[Stop。](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 當一個程式向 SDM 發送停止事件時,SDM 也會請求其他程式停止。

停止用於非同步通知 SDM 程式已停止。 通知 SDM 對於解釋器調試引擎很有用,有時調試程式中沒有代碼運行,因此[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)無法同步完成。 如果除錯引擎想要使用此同步通知,它必須從[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)`S_ASYNC_STOP`傳回 。

## <a name="requirements"></a>需求

標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll
