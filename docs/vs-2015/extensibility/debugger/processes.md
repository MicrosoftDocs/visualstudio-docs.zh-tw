---
title: 進程 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153673"
---
# <a name="processes"></a>處理序
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

就偵錯工具架構而言， **進程**：  
  
- 是一組程式的容器。 它相當類似于 Windows 進程，這是一組執行緒的容器。  
  
- 可以依名稱、識別碼或實體識別碼來識別其本身。  
  
- 可以列舉所有正在執行的程式 (及其執行緒) 。  
  
- 可以描述本身、其執行所在的埠，以及包含它的電腦。  
  
- 可以建立一或多個程式、終止它所建立的任何程式，或造成程式停止。  
  
- 會以 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 介面表示，此介面會在進程啟動時建立。 處理常式是由會話 debug manager (SDM) 或 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)啟動。  
  
  您可以藉由呼叫 [attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)，將 debug engine 附加至進程 (DE) 。 這表示，會將在進程中執行的所有可能程式附加到所有可能處理的程式。 例如，如果 common language runtime 取消附加至進程，它只會附加至執行 managed 程式碼的程式。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [執行緒](../../extensibility/debugger/threads.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [Debug 封裝](../../extensibility/debugger/debug-package.md)   
 [Debug 引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [附加](../../extensibility/debugger/reference/idebugprocess2-attach.md)
