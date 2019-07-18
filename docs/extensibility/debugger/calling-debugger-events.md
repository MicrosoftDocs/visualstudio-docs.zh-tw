---
title: 呼叫偵錯工具事件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7564010055218065a8971f40989af2152acd5d95
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332486"
---
# <a name="call-debugger-events"></a>呼叫偵錯工具事件
在偵錯工作階段的事件會發生特定的順序。

## <a name="discussion"></a>討論
 若要了解的偵錯引擎 (DE) 和工作階段的偵錯管理員 (SDM) 之間的呼叫模式，下列表示一般的偵錯工作階段中發生的事件的呼叫順序：

1. [附加和中斷連結至程式](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [啟動偵錯工具](../../extensibility/debugger/launching-the-debugger.md)

3. [終止程式](../../extensibility/debugger/terminating-a-program.md)

4. [建立中斷點](../../extensibility/debugger/creating-a-breakpoint.md)

5. [當中斷點繫結或變成未繫結](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [中斷點錯誤](../../extensibility/debugger/breakpoint-errors.md)

7. [叫用中斷點](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [刪除中斷點](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [進入中斷模式](../../extensibility/debugger/entering-break-mode.md)

10. [在中斷模式中逐步執行](../../extensibility/debugger/stepping-in-break-mode.md)

11. [在中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [例外狀況處理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>另請參閱
- [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)