---
title: 程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738202"
---
# <a name="programs"></a>Programs
在除錯器架構結構中,*程式*:

- 是一組線程和一組模組的容器。 程式在 Windows 作業系統中沒有單一類比。

     程式是一種子過程。 例如,在調試網站時,可以將腳本視為程式。 當腳本在腳本引擎進程中運行時,獨立於其他腳本,但它也有自己的一組線程。 除錯引擎 (DE) 附加到程式,而不是行程或線程。

- 可以標識自身及其正在運行的進程。 可以附加到程式,與創建它的 DE(如果有)分離並描述該程式。 程式還可以執行、停止、繼續和終止。

- 可以枚舉其所有線程。 程式還可以提供自己的拆解流,並可以枚舉給定文檔位置的所有代碼上下文。

- 由[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)介面表示,在附加程式之前創建,或作為附加過程的一部分,具體取決於實現。 當埠枚舉行程的程式時,每個程式都按照作為[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)的參數傳遞給的相應[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面創建。 雖然調試引擎還會創建`IDebugProgram2`介面來表示程式,但這些程式不是根據程式節點創建的。 DE`IDebugProgramNode2`創建的介面用於實際除錯,而埠建立的介面僅用於發現進程中正在運行的程式。

## <a name="see-also"></a>另請參閱
- [過程](../../extensibility/debugger/processes.md)
- [程式節點](../../extensibility/debugger/program-nodes.md)
- [模組](../../extensibility/debugger/modules.md)
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [偵錯引擎](../../extensibility/debugger/debug-engine.md)
- [文件位置](../../extensibility/debugger/document-position.md)
- [代碼內容](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
