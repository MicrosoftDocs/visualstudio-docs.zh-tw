---
title: "IDebugApplication 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication-interface"></a>IDebugApplication 介面
語言引擎，主機會公開使用的非遠端偵錯方法。  
  
 除了繼承自`IRemoteDebugApplication`、`IDebugApplication`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|設定應用程式的名稱。|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|告知偵錯處理序管理員在單一步驟模式中的語言引擎即將傳回其呼叫端。|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|會顯示偵錯工具 IDE 所指定的字串。|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|啟動預設偵錯工具 IDE，並會附加偵錯工作階段對此應用程式，如果其中一個未附加。|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|會導致目前的執行緒可封鎖，並傳送通知之中斷點的 IDE 偵錯工具。|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|造成此應用程式以釋放所有參考，並輸入非作用中狀態。|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|傳回目前應用程式的中斷旗標。|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|傳回目前執行的執行緒相關聯的執行緒。|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|提供非同步存取指定的同步偵錯作業。|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|將此應用程式中的堆疊框架的列舉值提供者。|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|移除此應用程式中的堆疊框架的列舉值提供者。|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|判斷目前執行的執行緒是否為偵錯工具執行緒。|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|提供偵錯工具執行緒中執行程式碼呼叫端的機制。|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|建立新的應用程式節點與特定文件提供者相關聯。|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|偵錯工具的一般事件的引發`IApplicationDebugger`介面。|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|會導致目前的執行緒可封鎖，並將錯誤的通知傳送至 IDE 偵錯工具。|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|判斷是否已登錄在 just-in-time (JIT) 偵錯工具。|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|決定如果 JIT 偵錯工具註冊到自動偵錯無聲主機。|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|將此應用程式全域運算式的內容提供者。|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|移除此應用程式全域運算式的內容提供者。|