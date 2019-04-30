---
title: 程式節點 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93c2d82ca683e7fb771ff3a443eb54746d4bde29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925256"
---
# <a name="program-nodes"></a>程式節點
在偵錯工具架構中，*計劃節點*:

- 是輕量型程式的描述。

- 可以識別本身和它正在中執行的程序。 程式節點可以附加、 中斷連結，並描述建立的偵錯引擎 (DE)，如果有的話。

- 由[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面，通常由 DE 或連接埠。 藉由呼叫程式的節點加入至連接埠[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 當程式節點加入至連接埠時，它會加入包含此程式節點所表示的程式處理序。

  啟動偵錯工作階段的一段時間，可根據的偵錯封裝，實作後程式節點用來建立對應的程式。 當查詢其程式的處理程序，就會列舉程式，一個用於每個程式節點。

  程式附加到之前，IDE 會要求程式的輕量級描述。 從 [程式] 節點，就可以取得此資訊。 在程式附加至時，IDE 會顯示更詳細的資訊，例如執行程式中的所有執行緒的清單。 這項資訊被取自程式本身。

## <a name="see-also"></a>另請參閱
- [程式](../../extensibility/debugger/programs.md)
- [處理序](../../extensibility/debugger/processes.md)
- [偵錯引擎](../../extensibility/debugger/debug-engine.md)
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)