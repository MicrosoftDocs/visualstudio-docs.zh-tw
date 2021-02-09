---
title: IDebugProgramNameChangedEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0640fa06b821c6679bc52c9f92a757cee6f0a580
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898745"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
當程式的名稱變更時，從 debug engine 傳送 (DE) 至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面，以報告程式的名稱已變更。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 **IDebugEvent2** 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 「取消」會建立並傳送此事件物件，以報告程式名稱變更。 當它附加至正在進行偵錯工具的程式時，會使用由 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送此事件。 自訂埠供應商會使用 I 介面傳送此事件。

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
