---
title: 附加和卸離程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e232a6f7fcb8813670ca6d949fdb6b3287bb79c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146451"
---
# <a name="attaching-and-detaching-to-a-program"></a>附加至程式及中斷連結程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

附加偵錯工具需要以適當的屬性傳送正確的方法和事件順序。  
  
## <a name="sequence-of-methods-and-events"></a>方法和事件的順序  
  
1. 會話 debug manager (SDM) 呼叫 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法。  
  
    根據 debug engine (DE) 進程模型， `IDebugProgramNodeAttach2::OnAttach` 方法會傳回下列其中一種方法，以決定接下來會發生什麼事。  
  
    如果 `S_FALSE` 傳回，則會成功將 debug engine 附加至程式。 否則，會呼叫 [attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 方法來完成附加程式。  
  
    如果 `S_OK` 傳回，則會在與 SDM 相同的進程中載入取消。 SDM 會執行下列工作：  
  
   1. 呼叫 [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) 以取得 DE 的引擎資訊。  
  
   2. 共同建立 DE。  
  
   3. 呼叫 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
2. DE 會將 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 傳送至具有屬性的 SDM `EVENT_SYNC` 。  
  
3. DE 會將 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 傳送至具有屬性的 SDM `EVENT_SYNC` 。  
  
4. DE 會將 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 傳送至具有屬性的 SDM `EVENT_SYNC_STOP` 。  
  
   從程式卸離是一個簡單的雙步驟程式，如下所示：  
  
5. SDM 呼叫卸 [離](../../extensibility/debugger/reference/idebugprogram2-detach.md)。  
  
6. DE 會傳送 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
