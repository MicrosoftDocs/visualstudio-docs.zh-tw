---
title: "附加和中斷連結至程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 71f678852b4d16d0b7c6f150abae03c6c4cdcad4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="attaching-and-detaching-to-a-program"></a>附加和中斷連結至程式
附加偵錯工具需要傳送正確的順序的方法和事件的適當的屬性。  
  
## <a name="sequence-of-methods-and-events"></a>順序的方法和事件  
  
1.  工作階段的偵錯管理員 (SDM) 呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。  
  
     根據偵錯引擎 (DE) 處理序模型，`IDebugProgramNodeAttach2::OnAttach`方法會傳回下列方法之一，以決定接下來的情況。  
  
     如果`S_FALSE`傳回，則偵錯引擎已順利附加到該程式。 否則，[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)呼叫方法來完成 attach 程序。  
  
     如果`S_OK`傳回，DE 是 SDM 相同的程序中載入。 SDM 會執行下列工作：  
  
    1.  呼叫[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)取得 DE 的引擎資訊。  
  
    2.  DE 會同時建立。  
  
    3.  呼叫[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
2.  DE 傳送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)來與 SDM`EVENT_SYNC`屬性。  
  
3.  DE 傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)來與 SDM`EVENT_SYNC`屬性。  
  
4.  DE 傳送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)來與 SDM`EVENT_SYNC_STOP`屬性。  
  
 從程式中斷連結的簡單、 兩步驟程序，如下所示：  
  
1.  SDM 呼叫[卸離](../../extensibility/debugger/reference/idebugprogram2-detach.md)。  
  
2.  DE 傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)