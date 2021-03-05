---
description: 當程式即將執行其第一個使用者程式碼指令時，debug engine (DE) 會將此介面傳送至會話 debug manager (SDM) 。
title: IDebugEntryPointEvent2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da733292407c93327374a4c6fa54c558d3202caa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153387"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
當程式即將執行其第一個使用者程式碼指令時，debug engine (DE) 會將此介面傳送至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這會將此介面實作為其一般作業的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 當正在進行程式設計的程式已載入，而且已準備好執行使用者程式碼的第一個指令時，取消會建立並傳送此事件物件。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="remarks"></a>備註
- 當程式即將執行第一個指令時，會傳送[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 。 例如， `IDebugEntryPoint2` 當程式即將執行使用者的函式時，就會傳送 `main` 。

 當取消傳送時 `IDebugEntryPointEvent2` ，目前的程式碼位置應該在使用者程式碼的第一個指令中，例如 `main` 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
