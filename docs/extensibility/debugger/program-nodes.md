---
title: 程式節點 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50ab93c31a340bf8a2f4e2deb5f202707d7826b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099599"
---
# <a name="program-nodes"></a>程式節點
偵錯工具就架構而言，**程式節點**:  
  
-   是輕量型程式的描述。  
  
-   可識別本身以及它正在執行中，並可附加至中斷連線，並描述建立它，如果有任何的偵錯引擎 (DE) 的程序。  
  
-   由[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面，通常由 DE 或連接埠所建立。 程式節點時，會新增至連接埠上，藉由呼叫[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 當程式節點加入至連接埠時，會將它加入至包含此程式的節點所代表的程式處理序。  
  
 啟動偵錯工作階段的一段時間，可根據的偵錯封裝，實作後程式節點用來建立對應的程式。 當處理程序針對它的程式查詢時，列舉程式，一個用於每個程式節點。  
  
 程式附加至 IDE 必須，該程式的輕量級描述。 可以從 [程式] 節點中取得這項資訊。 在程式附加至時，IDE 就必須顯示更詳細的資訊，例如執行在程式中的所有執行緒的清單。 這項資訊被取自程式本身。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [處理程序](../../extensibility/debugger/processes.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)