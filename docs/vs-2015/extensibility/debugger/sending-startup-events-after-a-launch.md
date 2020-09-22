---
title: 在啟動後傳送啟動事件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838965"
---
# <a name="sending-startup-events-after-a-launch"></a>在啟動後傳送啟動事件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

一旦將 debug engine (DE) 附加至程式之後，它就會將一連串的啟動事件傳送回 debug 會話。  
  
 傳送回錯會話的啟動事件包括下列各項：  
  
- 引擎建立事件。  
  
- 程式建立事件。  
  
- 執行緒建立和模組載入事件。  
  
- 載入完成事件，在程式碼載入並準備好執行時，但在執行任何程式碼之前傳送  
  
  > [!NOTE]
  > 當此事件繼續時，會初始化全域變數，並執行啟動常式。  
  
- 可能有其他執行緒建立和模組載入事件。  
  
- 進入點事件，表示程式已到達其主要進入點，例如 **main** 或 `WinMain` 。 如果取消附加至已在執行中的程式，通常不會傳送此事件。  
  
  先以程式設計的方式，先將會話 debug manager (SDM 傳送) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 介面（代表引擎建立事件），後面接著 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)（代表程式建立事件）。  
  
  這通常會接著一或多個 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 執行緒建立事件和 [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 模組載入事件。  
  
  當程式碼已載入且準備好要執行，但在執行任何程式碼之前，會先將 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 載入完成事件傳送給 SDM。 最後，如果程式尚未執行，則會傳送 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 進入點事件，指出程式已到達其主要進入點，並已準備好進行偵錯工具。  
  
## <a name="see-also"></a>另請參閱  
 [執行的控制](../../extensibility/debugger/control-of-execution.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)
