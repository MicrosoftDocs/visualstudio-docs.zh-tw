---
title: 附加與分離到程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739276"
---
# <a name="attaching-and-detaching-to-a-program"></a>附加及分離到程式
附加除錯器需要發送具有正確屬性的正確方法和事件序列。

## <a name="sequence-of-methods-and-events"></a>方法與事件的順序

1. 工作階段除錯管理員 (SDM) 呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。

    基於調試引擎 (DE) 過程`IDebugProgramNodeAttach2::OnAttach`模型, 該方法傳回以下方法之一,確定接下來會發生什麼。

    如果`S_FALSE`返回,調試引擎已成功連接到該程式。 否則,將調用[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)方法以完成附加過程。

    如果`S_OK`返回,DE 將載入到與 SDM 相同的進程中。 SDM 執行以下工作:

   1. 致電[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)獲取 DE 的引擎資訊。

   2. 共同創建 DE。

   3. 通話[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)。

2. DE 將[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)`EVENT_SYNC`發送到具有 屬性的 SDM。

3. DE 將[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)`EVENT_SYNC`發送到具有 屬性的 SDM。

4. DE 將[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)`EVENT_SYNC_STOP`發送到具有 屬性的 SDM。

   從程式分離是一個簡單的兩步過程,如下所示:

5. SDM 呼叫[分離](../../extensibility/debugger/reference/idebugprogram2-detach.md)。

6. DE 傳送[IDebugProgram 破壞事件2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)。

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
