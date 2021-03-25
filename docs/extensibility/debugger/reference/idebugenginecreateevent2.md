---
description: 當建立取消的實例時，debug engine (DE) 會將這個介面傳送至會話 debug manager (SDM) 。
title: IDebugEngineCreateEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da6b249581f4cf51d22ceb86eb0fd5837a42e8ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054357"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
當建立取消的實例時，debug engine (DE) 會將這個介面傳送至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這會將此介面實作為其一般作業的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的物件上執行， (SDM 會使用 `QueryInterface` 方法來存取 `IDebugEvent2` 介面) 。

## <a name="notes-for-callers"></a>呼叫者注意事項
 當取消已具現化時，會建立並傳送此事件物件。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugEngineCreateEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|抓取物件，該物件表示新建立的 debug engine (DE) 。|

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
