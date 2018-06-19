---
title: 在啟動後傳送啟動事件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6ffd1a47f4d1d82feecb35110151a8b32d7d245
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135750"
---
# <a name="sending-startup-events-after-a-launch"></a>在啟動後傳送啟動事件
在偵錯引擎 (DE) 會附加至程式之後，它會傳送一系列的啟動事件至偵錯工作階段。  
  
 啟動事件傳送到偵錯工作階段包括下列各項：  
  
-   引擎建立的事件。  
  
-   程式建立的事件。  
  
-   執行緒建立和模組載入事件。  
  
-   載入完成事件，傳送時的程式碼是載入並準備好執行，但任何程式碼執行之前  
  
    > [!NOTE]
    >  當此事件會繼續之後時，全域變數，並啟動程序執行。  
  
-   可能的其他執行緒建立和模組載入事件。  
  
-   項目點事件，以指示，程式已到達它的主要進入點，例如**Main**或`WinMain`。 此事件通常不傳送如果 DE 附加到已在執行中的程式。  
  
 以程式設計的方式，DE 首先會傳送工作階段的偵錯管理員 (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)介面代表引擎建立事件，後面跟著[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)表示程式建立事件。  
  
 這通常後面跟著一或多個[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)執行緒建立事件和[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)模組載入事件。  
  
 當程式碼會載入並準備好執行，但 DE 任何程式碼執行之前，傳送 SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)載入完成事件。 最後，如果尚未執行程式，DE 傳送[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)項目點事件，通知程式已達到其主要進入點，而且可供偵錯。  
  
## <a name="see-also"></a>另請參閱  
 [控制執行](../../extensibility/debugger/control-of-execution.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)