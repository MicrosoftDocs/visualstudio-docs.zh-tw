---
title: 啟動偵錯工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4ae4c7eed2ae5477be02384ebe7b7c45383eaffb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930015"
---
# <a name="launching-the-debugger"></a>啟動偵錯工具
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

啟動偵錯工具需要傳送的方法和事件及其適當的屬性使用正確的順序。  
  
## <a name="sequences-of-methods-and-events"></a>序列的方法和事件  
  
1.  工作階段的偵錯管理員 (SDM) 稱為選擇**偵錯** 功能表，然後選擇**開始**。 請參閱[啟動程式](../../extensibility/debugger/launching-a-program.md)如需詳細資訊。  
  
2.  SDM 呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。  
  
3.  根據偵錯引擎 (DE) 處理序模型，`IDebugProgramNodeAttach2::OnAttach`方法會傳回其中一種下列方法，用來決定接下來的情況。  
  
     如果`S_FALSE`會傳回虛擬機器正在載入為偵錯引擎 (DE)。  
  
     -或-  
  
     如果`S_OK`會傳回要載入的 DE 是同處理序的 SDM。 在 SDM 然後執行下列工作：  
  
    1.  呼叫[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)取得 DE 的引擎資訊。  
  
    2.  共同建立 DE。  
  
    3.  呼叫[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
4.  DE 傳送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)來使用 SDM`EVENT_SYNC`屬性。  
  
5.  DE 傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)來使用 SDM`EVENT_SYNC`屬性。  
  
6.  DE 傳送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)來使用 SDM`EVENT_SYNC`屬性。  
  
7.  DE 傳送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)來使用 SDM`EVENT_SYNC`屬性。  
  
8.  DE 傳送[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)來使用 SDM`EVENT_SYNC`屬性。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)   
 [啟動程式](../../extensibility/debugger/launching-a-program.md)
