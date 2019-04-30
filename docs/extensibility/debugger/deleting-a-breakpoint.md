---
title: 刪除中斷點 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8f2a4047fb44e2967e281becd90c78f66de9fdb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410022"
---
# <a name="deleting-a-breakpoint"></a>刪除中斷點
以下說明時刪除暫止中斷點的程序：

## <a name="deletion-process"></a>刪除程序
 工作階段的偵錯管理員 (SDM) 會呼叫[IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)從它的方法，以移除暫止中斷點及所有繫結的中斷點繫結。

> [!NOTE]
> 您也可以藉由呼叫刪除單一繫結的中斷點[IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)