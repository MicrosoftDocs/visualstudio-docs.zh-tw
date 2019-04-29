---
title: IDebugApplication 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8229f234f8a8ce607f36c48e070cb3d40a211d45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990832"
---
# <a name="idebugapplication-interface"></a>IDebugApplication 介面
公開非遠端偵錯的方法，以供語言引擎和主機。  
  
 除了繼承自方法`IRemoteDebugApplication`，則`IDebugApplication`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|設定應用程式的名稱。|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|通知程序的偵錯管理員在單一步驟模式中的語言引擎即將返回其呼叫端。|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|會導致偵錯工具 IDE 會顯示指定的字串。|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|啟動預設偵錯工具 IDE，並將偵錯工作階段附加至這個應用程式而言，如果其中一個尚未附加。|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|讓目前的執行緒封鎖並傳送通知之中斷點的偵錯工具 IDE。|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|造成此應用程式以發行所有參考，然後輸入 非作用中狀態。|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|傳回目前應用程式的中斷旗標。|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|傳回與目前執行的執行緒相關聯的執行緒。|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|提供指定的同步偵錯作業的非同步存取。|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|將此應用程式中的堆疊框架的列舉值提供者。|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|移除此應用程式中的堆疊框架的列舉值提供者。|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|判斷目前執行中的執行緒是否為偵錯工具執行緒。|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|提供一個機制，讓呼叫者在偵錯工具執行緒中執行程式碼。|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|建立新的應用程式節點與特定文件提供者相關聯。|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|偵錯工具的一般事件，就會引發`IApplicationDebugger`介面。|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|讓目前的執行緒封鎖，並將錯誤的通知傳送至偵錯工具 IDE。|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|判斷是否已登錄在 just-in-time (JIT) 偵錯工具。|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|判斷 JIT 偵錯工具已向自動偵錯無聲主機。|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|將此應用程式全域運算式的內容提供者。|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|移除此應用程式全域運算式的內容提供者。|