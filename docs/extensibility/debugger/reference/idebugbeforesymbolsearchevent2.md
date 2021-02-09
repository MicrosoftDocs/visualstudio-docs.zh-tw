---
title: IDebugBeforeSymbolSearchEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb185e098d76184d3a74df380eb8a5e66bc699df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869956"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Debug engine (DE) 會將這個介面傳送至會話 debug manager (SDM) ，在符號載入期間設定狀態列訊息。

## <a name="syntax"></a>Syntax

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 當這個介面必須在符號載入期間設定狀態列訊息時，就會執行這個介面。 這個介面只會由使用或屬於腳本解譯器一部分的偵錯工具引擎來執行。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的物件上執行， (SDM 使用 **QueryInterface** 來存取 **IDebugEvent2** 介面) 。

## <a name="notes-for-callers"></a>呼叫者注意事項
 當此事件物件必須在符號載入期間設定狀態列訊息時，即會建立並傳送此事件物件。 當附加至要進行偵錯工具的程式時，會使用由 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件。

## <a name="methods"></a>方法
 下表顯示的方法 `IDebugBeforeSymbolSearchEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|抓取目前正在進行調試的模組名稱。|

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
