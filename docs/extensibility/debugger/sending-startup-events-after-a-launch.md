---
title: "在啟動後傳送啟動事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 65e05d7da2acf5bd3eaf8dab1e3781d3d5b244a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>請參閱  
 [控制執行](../../extensibility/debugger/control-of-execution.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)