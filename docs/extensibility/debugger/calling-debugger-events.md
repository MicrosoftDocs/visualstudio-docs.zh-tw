---
title: 呼叫除錯器事件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 869bd87952aebf8ad640c5aeb439c9e99929f4c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739171"
---
# <a name="call-debugger-events"></a>呼叫除錯器事件
調試會話中的事件按特定順序發生。

## <a name="discussion"></a>討論區
 要瞭解除錯引擎 (DE) 與工作階段除錯管理員 (SDM) 之間的呼叫模式,以下表示典型除錯工作階段中發生的事件的呼叫順序:

1. [附加及分離到程式](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [啟動除錯器](../../extensibility/debugger/launching-the-debugger.md)

3. [終止程式](../../extensibility/debugger/terminating-a-program.md)

4. [建立斷點](../../extensibility/debugger/creating-a-breakpoint.md)

5. [當斷點繫結或變為未綁定時](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [斷點錯誤](../../extensibility/debugger/breakpoint-errors.md)

7. [Hitting a breakpoint](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [刪除斷點](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [進入中斷模式](../../extensibility/debugger/entering-break-mode.md)

10. [進一步進入中斷模式](../../extensibility/debugger/stepping-in-break-mode.md)

11. [中斷模式下的運算](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [例外處理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>另請參閱
- [建立自訂除錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
