---
title: 處理序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 75230740e84bb6660629b38e84df56fa8e5c1856
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102755"
---
# <a name="processes"></a>處理序
偵錯工具就架構而言，**程序**:  
  
-   是一組程式的容器。 它是密切類似於 Windows 處理序，是一組執行緒的容器。  
  
-   可以識別本身的名稱、 識別碼或實體的識別項。  
  
-   所有執行中的程式 （和其執行緒），可以列舉。  
  
-   可以描述本身、 執行中，連接埠和包含它的電腦。  
  
-   可以建立一或多個程式終止的任何程式，它會建立，或造成程式停止。  
  
-   由[IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)時啟動處理序所建立的介面。 處理程序由其中一個工作階段偵錯管理員 (SDM) 啟動或[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
 偵錯封裝可以附加至處理序的偵錯引擎 (DE) 藉由呼叫[附加](../../extensibility/debugger/reference/idebugprocess2-attach.md)。 這表示 DE 附加所有可能的程式，它可以處理程序中執行。 例如，如果 common language runtime DE 附加至處理序，它會將附加，才能執行 managed 程式碼中的程式。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [執行緒](../../extensibility/debugger/threads.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [偵錯封裝](../../extensibility/debugger/debug-package.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)