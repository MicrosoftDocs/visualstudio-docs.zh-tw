---
title: 刪除中斷點 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738947"
---
# <a name="deleting-a-breakpoint"></a>刪除斷點
下面描述了刪除掛起的斷點時的過程:

## <a name="deletion-process"></a>移除過程
 工作階段調試管理員 (SDM) 呼叫[IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)方法,以刪除掛起的斷點和所有綁定斷點。

> [!NOTE]
> 單個綁定斷點也可以通過調用[IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)刪除。

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
