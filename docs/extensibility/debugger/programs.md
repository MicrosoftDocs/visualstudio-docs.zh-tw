---
title: 程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd3d1c1e72524c393fdb3adc4477ea9ae374fbfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="programs"></a>Programs
偵錯工具就架構而言，**程式**:  
  
-   是一組執行緒和模組的一組的容器。 程式會在 Windows 作業系統中有沒有單一的類比。  
  
     程式是一種處理序。 例如，當您偵錯的網站，指令碼可視為程式。 雖然指令碼會執行指令碼引擎處理，獨立於其他指令碼，它也有自己的執行緒集。 偵錯引擎 (DE) 附加至程式中，和不能處理程序或執行緒。  
  
-   可識別本身以及它正在執行中，並可附加至中斷連線，並說明如果有的話，請建立它，DE 的程序。 程式執行、 停止、 繼續和終止。  
  
-   可以列舉其所有的執行緒。 程式也可以提供自己的反組譯碼資料流，然後可以列舉給定文件位置的所有程式碼內容。  
  
-   由[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)介面，建立程式已連接之前，或做為附加的處理序，視實作而定的一部分。 根據對應時的連接埠列舉處理序的程式，會建立每個程式[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)傳遞做為引數的介面[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 雖然偵錯引擎也會產生`IDebugProgram2`介面來代表程式，這些程式不會建立符合程式節點。 `IDebugProgramNode2` DE 所建立的介面可用來實際偵錯時所建立的連接埠僅適用於探索處理程序中執行的程式。  
  
## <a name="see-also"></a>另請參閱  
 [處理程序](../../extensibility/debugger/processes.md)   
 [程式節點](../../extensibility/debugger/program-nodes.md)   
 [模組](../../extensibility/debugger/modules.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [文件位置](../../extensibility/debugger/document-position.md)   
 [程式碼內容](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)