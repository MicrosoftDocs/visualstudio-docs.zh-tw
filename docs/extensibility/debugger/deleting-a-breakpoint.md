---
title: 刪除中斷點 |Microsoft Docs
description: 瞭解當暫止中斷點刪除時，會話偵錯工具管理員如何移除暫止中斷點，以及所有系結中斷點的繫結項目。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 061175326a19af1866262421b381eb14267c7efd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915553"
---
# <a name="deleting-a-breakpoint"></a>刪除中斷點
以下說明刪除暫止中斷點時的程式：

## <a name="deletion-process"></a>刪除進程
 會話 debug manager (SDM) 會呼叫 [IDebugPendingBreakpoint2：:D elete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 方法，以移除暫止中斷點以及所有與其系結的系結中斷點。

> [!NOTE]
> 單一系結中斷點也可以透過呼叫 [IDebugBoundBreakpoint2：:D elete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)來刪除。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
