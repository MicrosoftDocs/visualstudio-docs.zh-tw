---
title: 通知埠 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738323"
---
# <a name="notify-the-port"></a>通知連接埠
啟動程式後,必須通知埠,如下所示:

1. 當埠收到新的程式節點時,它將程式創建事件發送回調試會話。 該事件帶有一個表示程式的介面。

2. 除錯工作階段查詢可以附加到的除錯引擎 (DE) 識別碼的程式。

3. 除錯工作階段檢查 DE 是否位於該程式的允許 D 清單中。 除錯工作階段從解決方案的活動程式設置獲取此清單,該設置最初由調試包傳遞給它。

    DE 必須位於允許清單中,否則 DE 將不會附加到程式。

   在程式設計上,當埠首次收到新的程式節點時,它會創建一個[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)介面來表示程式。

> [!NOTE]
> 這不應與調試引擎 (DE) 以後`IDebugProgram2`創建的介面混淆。

 埠透過 COM`IConnectionPoint`介面將[IDebug ProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)程式建立事件發送回工作階段調試管理員 (SDM)。

> [!NOTE]
> 這不應與`IDebugProgramCreateEvent2`DE 稍後發送的介面混淆。

 除了事件介面本身外,埠還發送[IDebugPort2、IDebugProcess2](../../extensibility/debugger/reference/idebugport2.md)和[IDebug Program2](../../extensibility/debugger/reference/idebugprogram2.md)介面,分別表示埠、程序[IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)和程式。 SDM 呼叫[IDebugProgram2::取得引擎資訊](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)以取得可以調試程式的 DE GUID。 GUID 最初從[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面獲得。

 SDM 檢查 DE 是否位於允許的 DE 清單中。 SDM 從解決方案的活動程式設置獲取此清單,該設置最初由調試包傳遞給它。 DE 必須位於允許的清單中,否則不會附加到程式。

 一旦 DE 的標識已知,SDM 就可以將其附加到程式。

## <a name="see-also"></a>另請參閱
- [啟動程式](../../extensibility/debugger/launching-a-program.md)
- [啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)
- [除錯工作](../../extensibility/debugger/debugging-tasks.md)
