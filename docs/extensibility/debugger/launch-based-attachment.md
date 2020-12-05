---
title: 以啟動為基礎的附件 |Microsoft Docs
description: 深入瞭解以啟動為基礎的程式附件（自動），並遵循與手動附件類似的路徑。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7e041c692a833b7d0a1891c078388a3f5b2d11e4
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606667"
---
# <a name="launch-based-attachment"></a>以啟動為基礎的附件
以啟動為基礎的程式附件是自動的。 當裝載程式的進程由 SDM 啟動時，以啟動為基礎的附件會遵循與手動附件方法類似的路徑。 如需詳細資訊，請參閱 [附加至程式](../../extensibility/debugger/attaching-to-the-program.md)。

## <a name="the-attaching-process"></a>附加進程
 主要差異在於 **附加** 呼叫之後的事件順序，如下所示：

1. 將 **IDebugEngineCreateEvent2** 事件物件傳送至 SDM。 如需詳細資訊，請參閱 [傳送事件](../../extensibility/debugger/sending-events.md)。

2. `IDebugProgram2::GetProgramId`在傳遞至 **附加** 方法的 **IDebugProgram2** 介面上呼叫方法。

3. 傳送 **IDebugProgramCreateEvent2** 事件物件，以通知 SDM 已建立本機 **IDebugProgram2** 物件來代表要解除的程式。

4. 傳送 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 事件物件來通知 SDM，為啟動的進程建立新的執行緒。

## <a name="see-also"></a>另請參閱
- [傳送所需的事件](../../extensibility/debugger/sending-the-required-events.md)
- [啟用要進行調試的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
