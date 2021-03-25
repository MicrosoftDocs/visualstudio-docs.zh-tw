---
title: 呼叫偵錯工具事件 |Microsoft Docs
description: 調試會話中的事件會以特定順序發生。 本文列出一般偵錯工具會話中發生之事件的呼叫順序。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b0c3169039115432758cfdcd3f0612c3578b74c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055046"
---
# <a name="call-debugger-events"></a>呼叫偵錯工具事件
調試會話中的事件會以特定順序發生。

## <a name="discussion"></a>討論
 若要瞭解 debug engine (DE) 和會話 debug manager (SDM) 之間的呼叫模式，以下代表在一般的偵錯工具會話中發生之事件的呼叫順序：

1. [附加和卸離程式](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [啟動偵錯工具](../../extensibility/debugger/launching-the-debugger.md)

3. [終止程式](../../extensibility/debugger/terminating-a-program.md)

4. [建立中斷點](../../extensibility/debugger/creating-a-breakpoint.md)

5. [當中斷點系結或變成未系結時](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [中斷點錯誤](../../extensibility/debugger/breakpoint-errors.md)

7. [Hitting a breakpoint](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [刪除中斷點](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [進入中斷模式](../../extensibility/debugger/entering-break-mode.md)

10. [在中斷模式中逐步執行](../../extensibility/debugger/stepping-in-break-mode.md)

11. [中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [例外狀況處理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>另請參閱
- [建立自訂的調試引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
