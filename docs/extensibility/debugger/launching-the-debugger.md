---
title: 啟動除錯器 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738453"
---
# <a name="launch-the-debugger"></a>啟動除錯器
啟動除錯器需要發送正確的方法和事件序列及其正確的屬性。

## <a name="sequences-of-methods-and-events"></a>方法與事件的順序

1. 通過選擇**調試**選單,然後選擇 **「開始」** 來呼叫工作階段除錯管理員 (SDM)。 有關詳細資訊,請參閱[啟動程式](../../extensibility/debugger/launching-a-program.md)。

2. SDM 調用[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。

3. 基於調試引擎 (DE) 過程`IDebugProgramNodeAttach2::OnAttach`模型, 該方法傳回以下方法之一,確定接下來會發生什麼。

     如果`S_FALSE`返回,調試引擎 (DE) 將在虛擬機器過程中載入。

     -或-

     如果`S_OK`返回,DE 將在 SDM 的進程中載入。 然後,SDM 執行以下任務:

    1. 致電[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)獲取 DE 的引擎資訊。

    2. 共同創建 DE。

    3. 通話[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)。

4. DE 將[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)`EVENT_SYNC`發送到具有 屬性的 SDM。

5. DE 將[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)`EVENT_SYNC`發送到具有 屬性的 SDM。

6. DE 將[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)`EVENT_SYNC`發送到具有 屬性的 SDM。

7. DE 將[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)`EVENT_SYNC`發送到具有 屬性的 SDM。

8. DE 將[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)`EVENT_SYNC`發送到具有 屬性的 SDM。

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
- [啟動程式](../../extensibility/debugger/launching-a-program.md)
