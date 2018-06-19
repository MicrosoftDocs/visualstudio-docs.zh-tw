---
title: 啟動偵錯工具 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2606e0f6c7d5dfe17e4c82528c36b3f7cdc26c5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108926"
---
# <a name="launching-the-debugger"></a>啟動偵錯工具
啟動偵錯工具需要傳送正確的順序的方法和事件的適當的屬性。  
  
## <a name="sequences-of-methods-and-events"></a>序列的方法和事件  
  
1.  藉由選擇稱為工作階段的偵錯管理員 (SDM)**偵錯** 功能表，然後選擇**啟動**。 請參閱[啟動程式](../../extensibility/debugger/launching-a-program.md)如需詳細資訊。  
  
2.  SDM 呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。  
  
3.  根據偵錯引擎 (DE) 處理序模型，`IDebugProgramNodeAttach2::OnAttach`方法會傳回下列方法之一，以決定接下來的情況。  
  
     如果`S_FALSE`傳回，偵錯引擎 (DE) 是要載入正在虛擬機器。  
  
     -或-  
  
     如果`S_OK`會傳回要載入，則為 DE 同處理序的 SDM。 SDM 然後執行下列工作：  
  
    1.  呼叫[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)取得 DE 的引擎資訊。  
  
    2.  DE 會同時建立。  
  
    3.  呼叫[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
4.  DE 傳送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)來與 SDM`EVENT_SYNC`屬性。  
  
5.  DE 傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)來與 SDM`EVENT_SYNC`屬性。  
  
6.  DE 傳送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)來與 SDM`EVENT_SYNC`屬性。  
  
7.  DE 傳送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)來與 SDM`EVENT_SYNC`屬性。  
  
8.  DE 傳送[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)來與 SDM`EVENT_SYNC`屬性。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)   
 [啟動程式](../../extensibility/debugger/launching-a-program.md)