---
title: 基於啟動的附件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738467"
---
# <a name="launch-based-attachment"></a>建基於開機的附件
基於啟動的程式附件是自動的。 當託管程式的進程由 SDM 啟動時,基於啟動的附件遵循類似於手動附件方法的路徑。 有關詳細資訊,請參閱[附加到程式](../../extensibility/debugger/attaching-to-the-program.md)。

## <a name="the-attaching-process"></a>附加過程
 主要區別是**附加**調用后的事件序列,如下所示:

1. 將**IDebugEngineCreateEvent2**事件物件發送到 SDM。 有關詳細資訊,請參閱[傳送事件](../../extensibility/debugger/sending-events.md)。

2. 調用傳遞給`IDebugProgram2::GetProgramId`**附加**方法的**IDebugProgram2**介面上的方法。

3. 發送**IDebugProgramCreateEvent2**事件物件,通知 SDM 本地**IDebugProgram2**物件是為了向 DE 表示程式。

4. 發送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)事件物件,通知 SDM 為啟動的進程創建新線程。

## <a name="see-also"></a>另請參閱
- [傳送所需事件](../../extensibility/debugger/sending-the-required-events.md)
- [開啟對程式進行除錯](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
