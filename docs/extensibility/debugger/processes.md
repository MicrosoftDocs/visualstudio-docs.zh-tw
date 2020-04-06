---
title: 流程 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738243"
---
# <a name="processes"></a>處理序
在除錯器架構結構中,*行程*:

- 是一組程式的容器。 它與 Windows 進程非常相似,Windows 進程是一組線程的容器。

- 可以按名稱、標識碼或物理標識碼識別自身。

- 可以枚舉所有正在運行的程式(及其線程)。

- 可以描述自身、正在運行的埠以及包含它的計算機。

- 可以創建一個或多個程式、終止它創建的任何程式,或導致程式停止。

- 由[IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)介面表示,該介面是在啟動進程時創建的。 進程由工作階段調試管理員 (SDM) 或[Launch 暫停](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)啟動。

  除錯套件可以透過調用[Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)將除錯引擎 (DE) 附加到行程,這意味著 DE 附加到它可以處理的進程中運行的所有可能的程式。 例如,如果通用語言運行時 DE 附加到進程,則它僅附加到運行託管代碼的程式。

## <a name="see-also"></a>另請參閱
- [Programs](../../extensibility/debugger/programs.md)
- [執行緒](../../extensibility/debugger/threads.md)
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [除錯套件](../../extensibility/debugger/debug-package.md)
- [偵錯引擎](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [附加](../../extensibility/debugger/reference/idebugprocess2-attach.md)
