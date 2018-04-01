---
title: IDebugBeforeSymbolSearchEvent2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4ec023384ab95e72d0341fb728eb0fd6a4f58480
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
偵錯引擎 (DE) 過程中傳送此介面至工作階段的偵錯管理員 (SDM) 的狀態設列訊息符號載入。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 當它必須在符號載入期間設定狀態列訊息 DE 會實作這個介面。 只能由偵錯引擎會處理或屬於指令碼解譯器會實作這個介面。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件上 (SDM 使用**QueryInterface**存取**IDebugEvent2**介面)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 建立和傳送此事件的物件，它必須在符號載入期間設定狀態列訊息時。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，SDM 所提供的回呼函式。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugBeforeSymbolSearchEvent2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|擷取目前所偵錯之模組的名稱。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll