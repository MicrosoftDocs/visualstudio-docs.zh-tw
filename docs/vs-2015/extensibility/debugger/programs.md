---
title: 程式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c6db9d45f9bb421738b71e630482cbbb8f6525c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500451"
---
# <a name="programs"></a>Programs
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[程式](https://docs.microsoft.com/visualstudio/extensibility/debugger/programs)。  
  
偵錯工具就架構而言，**程式**:  
  
-   是一組執行緒和一組模組的容器。 程式已在 Windows 作業系統中有沒有單一的比喻。  
  
     程式是一種表示子處理序。 比方說，當您偵錯網站時，指令碼可視為程式。 雖然指令碼會執行指令碼引擎處理序中，獨立於其他指令碼，它也有它自己的執行緒集。 偵錯引擎 (DE) 附加至程式中，而不必處理程序或執行緒。  
  
-   可以識別本身和它正在執行中，並可以附加至要卸離，並說明如果有的話，請建立它，DE 的程序。 程式可以執行、 停止、 繼續和終止。  
  
-   可以列舉其所有的執行緒。 程式也可以提供自己的反組譯碼資料流，並可以列舉的特定文件位置的所有程式碼內容。  
  
-   由[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)介面，建立的程式附加之前，或做為附加的處理序，視實作而定的一部分。 連接埠列舉處理序的程式，每個程式會建立符合對應[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)傳遞做為引數的介面[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 同時也建立偵錯引擎`IDebugProgram2`介面來代表程式，這些程式不會建立根據程式節點。 `IDebugProgramNode2`規定所建立的介面會用於實際偵錯時所建立的連接埠僅用於探索處理序中執行的程式。  
  
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

