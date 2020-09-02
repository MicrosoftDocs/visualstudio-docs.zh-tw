---
title: 程式節點 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153651"
---
# <a name="program-nodes"></a>程式節點
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

就偵錯工具架構而言， **程式節點**：  
  
- 是程式的輕量描述。  
  
- 可以識別其本身及其執行所在的進程，並可將它附加至、卸離和描述 debug engine (移除建立它的) （如果有的話）。  
  
- 是以 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 介面表示，通常是由 DE 或埠所建立。 藉由呼叫 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)，將程式節點新增至埠。 當程式節點新增至埠時，它會新增至包含此程式節點所代表之程式的進程。  
  
  當偵錯工具啟動之後，就會根據 debug 封裝的執行，使用程式節點來建立對應的程式。 針對程式查詢程式時，系統會列舉程式，每個程式節點各有一個程式。  
  
  將程式附加至之前，IDE 只需要程式的輕量描述。 您可以從程式節點取得此資訊。 將程式附加至之後，IDE 需要顯示更詳細的資訊，例如在程式中執行的所有線程清單。 這項資訊是從程式本身取得。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [過程](../../extensibility/debugger/processes.md)   
 [Debug 引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
