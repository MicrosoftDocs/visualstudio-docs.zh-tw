---
title: 程式節點 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738213"
---
# <a name="program-nodes"></a>程式節點
在除錯器架構結構中,*程式節點*:

- 是程式的輕量級描述。

- 可以標識自身及其正在運行的進程。 可以附加到、分離程式節點並描述創建它的調試引擎 (DE)(如果有)。

- 由[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面表示,通常由 DE 或埠創建。 程序節點通過調用[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)添加到埠。 將程式節點添加到埠時,該節點將添加到包含此程式節點表示的程序的進程。

  除錯工作階段啟動後的某個時間,根據調試包的實現,程式節點用於創建相應的程式。 當查詢進程的程式時,將枚舉程式,每個程式節點一個程式。

  在將程式附加到之前,IDE只需要該程序的輕量級說明。 此資訊可以從程序節點獲取。 附加程式後,IDE 將顯示更詳細的資訊,例如程式中運行的所有線程的清單。 此資訊是從程式本身獲取的。

## <a name="see-also"></a>另請參閱
- [Programs](../../extensibility/debugger/programs.md)
- [過程](../../extensibility/debugger/processes.md)
- [偵錯引擎](../../extensibility/debugger/debug-engine.md)
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
