---
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f563d8cd40a8c30542b1aa93fa22afc8d161a52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923737"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) 的狀態設定，訊息列符號載入期間，傳送這個介面。

## <a name="syntax"></a>語法

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 DE 實作這個介面，它必須在符號載入期間設定狀態列訊息時。 只偵錯引擎使用，或屬於指令碼解譯器會實作這個介面。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上 (使用 SDM **QueryInterface**若要存取**IDebugEvent2**介面)。

## <a name="notes-for-callers"></a>呼叫端資訊
 DE 會建立並傳送這個事件物件，它必須在符號載入期間設定狀態列訊息時。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，在 SDM 所提供的回呼函式。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugBeforeSymbolSearchEvent2`。

|方法|描述|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|擷取目前所偵錯的模組名稱。|

## <a name="requirements"></a>需求
 標頭：Msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll