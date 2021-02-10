---
title: 程式 |Microsoft Docs
description: 本文說明 Visual Studio 中偵錯工具架構中程式的定義和角色。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5205dba6cddf104d0cb05f01acbc43f6927acaaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948422"
---
# <a name="programs"></a>程式
在偵錯工具架構中， *程式*：

- 是一組執行緒和一組模組的容器。 在 Windows 作業系統中，程式沒有任何單一的比喻。

     程式是一種子流程。 例如，當您在進行網站的偵錯工具時，可以將腳本視為程式。 雖然腳本會在腳本引擎進程中執行（與其他腳本無關），但它也有自己的一組執行緒。 Debug engine (DE) 附加至程式，而不是處理常式或執行緒。

- 可以識別自己及其執行所在的進程。 程式可以附加至、卸離，以及描述建立的程式（如果有的話）。 程式也可以執行、停止、繼續和終止。

- 可以列舉其所有線程。 程式也可以提供自己的反組解碼資料流程，也可以列舉指定檔位置的所有程式碼內容。

- 會以 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 介面表示，在附加程式之前建立，或作為附加程式的一部分，視執行而定。 當埠列舉進程的程式時，會根據將作為引數傳遞至[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)的對應[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面建立每個程式。 雖然 debug 引擎也 `IDebugProgram2` 會建立介面來代表程式，但不會根據程式節點來建立這些程式。 DE 所建立的介面可用於 `IDebugProgramNode2` 實際的偵錯工具，而由埠所建立的介面則只用于探索進程中正在執行的程式。

## <a name="see-also"></a>另請參閱
- [處理序](../../extensibility/debugger/processes.md)
- [程式節點](../../extensibility/debugger/program-nodes.md)
- [單元](../../extensibility/debugger/modules.md)
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [Debug 引擎](../../extensibility/debugger/debug-engine.md)
- [檔位置](../../extensibility/debugger/document-position.md)
- [程式碼內容](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
