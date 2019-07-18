---
title: 處理程序 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153673"
---
# <a name="processes"></a>處理序
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

偵錯工具就架構而言，**程序**:  
  
- 是一組程式的容器。 它是密切類似於 Windows 處理程序，也就是執行緒的一組的容器。  
  
- 可以依名稱、 識別碼或實體的識別碼識別本身。  
  
- 可以列舉所有執行中的程式 （和其執行緒）。  
  
- 可以描述本身、 執行中，連接埠和包含它的電腦。  
  
- 可以建立一個或多個程式終止任何它所建立的應用程式，或造成程式停止。  
  
- 由[IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)時啟動處理序所建立的介面。 啟動處理序的其中一個工作階段偵錯管理員 (SDM) 或[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
  偵錯封裝可以附加至處理序的偵錯引擎 (DE) 藉由呼叫[附加](../../extensibility/debugger/reference/idebugprocess2-attach.md)。 這表示 DE 附加至所有可能的程式，它可以處理處理序中執行。 例如，如果 common language runtime DE 附加至處理序，它會連結才能執行 managed 程式碼的程式。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [執行緒](../../extensibility/debugger/threads.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [偵錯封裝](../../extensibility/debugger/debug-package.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
