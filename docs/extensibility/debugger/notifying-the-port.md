---
title: 通知埠 |Microsoft Docs
description: 瞭解如何在啟動程式之後通知埠。 本文包含詳細的描述。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d1fdf09859c8b943eb71a403f49b29dc8b315503
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884906"
---
# <a name="notify-the-port"></a>通知埠
啟動程式之後，必須通知埠，如下所示：

1. 當埠收到新的程式節點時，它會將程式建立事件傳送回 debug 會話。 事件會以代表程式的介面來傳送。

2. Debug 會話會查詢程式中的偵錯工具識別碼， (可以附加至的) 。

3. Debug 會話會檢查是否已在該程式允許的 DEs 清單上進行取消。 Debug 會話會從解決方案的作用中程式設定取得這份清單，此清單最初是由 debug 封裝傳遞給它。

    DE 必須在允許清單上，否則 DE 將不會附加至程式。

   以程式設計的方式，當埠第一次收到新的程式節點時，它會建立 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 介面來代表程式。

> [!NOTE]
> 這不應該與 `IDebugProgram2` debug engine (DE) 中稍後建立的介面混淆。

 埠會透過 COM 介面，將 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 程式建立事件傳回給會話 debug MANAGER (SDM) `IConnectionPoint` 。

> [!NOTE]
> 這不應該與 `IDebugProgramCreateEvent2` 稍後由 DE 傳送的介面混淆。

 除了事件介面本身，埠會傳送 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)、 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)和 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 介面，分別代表埠、進程和程式。 SDM 會呼叫 [IDebugProgram2：： GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) ，以取得可對程式進行 debug 錯的 DE 的 GUID。 GUID 最初是從 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 介面取得。

 SDM 會檢查是否已在允許的 DEs 清單上進行取消。 SDM 會從方案的作用中程式設定取得這份清單，此清單最初是由 debug 封裝傳遞給它。 DE 必須在允許清單上，否則它將不會附加至程式。

 一旦已知解除的身分識別之後，就可以將 SDM 附加至程式。

## <a name="see-also"></a>另請參閱
- [啟動程式](../../extensibility/debugger/launching-a-program.md)
- [在啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)
- [調試作業](../../extensibility/debugger/debugging-tasks.md)
