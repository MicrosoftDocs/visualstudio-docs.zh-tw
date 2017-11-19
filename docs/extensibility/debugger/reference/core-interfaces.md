---
title: "核心介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 367917032b836ce6a7d07cf3eba85db14464a957
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="core-interfaces"></a>核心介面
下列介面會使用擴充偵錯工具的核心介面[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]。  
  
## <a name="discussion"></a>討論  
 若要建立的偵錯引擎 (DE) 主要用於這些介面。 它們會依以下類別：  
  
-   [中斷點](#Breakpoints)  
  
-   [內容](#Contexts)  
  
-   [核心伺服器](#CoreServer)  
  
-   [偵錯引擎](#DebugEngines)  
  
-   [文件](#Documents)  
  
-   [事件](#Events)  
  
-   [運算式](#Expressions)  
  
-   [記憶體](#Memory)  
  
-   [模組](#Modules)  
  
-   [連接埠](#Ports)  
  
-   [處理序](#Processes)  
  
-   [程式](#Programs)  
  
-   [屬性](#Properties)  
  
-   [堆疊框架](#StackFrames)  
  
-   [執行緒](#Threads)  
  
-   [類型的視覺化檢視](#TypeVisualizers)  
  
 可以實作介面的實體包括：  
  
-   偵錯引擎 (DE)  
  
-   連接埠供應商 (PS)  
  
-   運算式評估工具 (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a>中斷點  
 有關這些介面實作] 和 [追蹤的中斷點。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|表示繫結至記憶體位置中斷點。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|傳送 DE 中斷點繫結的記憶體位置時。|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|表示中斷點要求的文件總和檢查碼。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|當中斷點無法繫結至記憶體位置時，由 DE 傳送。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|在到達中斷點時，由 DE 傳送。|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|表示中斷點; 的要求用來建立暫止中斷點。|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|表示中斷點; 的要求用來建立暫止中斷點。|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|代表用來將中斷點繫結的資訊。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|傳送 DE 中斷點解除繫結時的記憶體位置。|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|代表無效的中斷點 (傳回`IDebugBreakpointErrorEvent2`)。|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|表示無效的中斷點解析資訊。|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|表示函式在已設定中斷點的位置。|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|表示繫結; 中斷點用來建立繫結的中斷點。|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|代表一組繫結的中斷點列舉型別。|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|代表一組可能未繫結至記憶體位置的中斷點列舉型別。|  
  
##  <a name="Contexts"></a>內容  
 這些介面代表各種偵錯程式內的內容。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|表示程式碼指示的開始位置。|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|擴充[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)介面，以擷取模組和處理序的介面。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS DE|代表文件中的位置。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示要在其中評估運算式的內容。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示在記憶體中的位元組集合的起始位置。|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|代表於中斷點或例外狀況的堆疊框架內容。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|代表於中斷點或例外狀況的堆疊框架內容。|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|表示列舉型別資料集的程式碼內容。|  
  
##  <a name="CoreServer"></a>核心伺服器  
 這些介面代表一個程式正在偵錯的電腦。 這些由實作[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]但可以由偵錯引擎呼叫。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|提供存取權的連接埠和通訊埠供應商，以及電腦的相關資訊。|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|代表[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)支援遠端偵錯。|  
  
##  <a name="DebugEngines"></a>偵錯引擎  
 這些介面代表偵錯引擎以及與其相關聯的事件。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|表示自訂偵錯引擎。|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|表示支援載入符號、 JustMyCode 和例外狀況的自訂偵錯引擎。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|表示已準備好處理偵錯工作傳送 DE 每個新執行個體。|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|表示支援啟動程式的自訂偵錯引擎。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE、 PS|代表會處理多個偵錯引擎的程式節點。|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|提供方法讓偵錯引擎來取得介面執行緒、 程式或堆疊框架 SDM。|  
  
##  <a name="Documents"></a>文件  
 這些介面代表文件 （來源檔案） 和其相關聯的項目。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE 傳送以要求開啟的文件。|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|表示反組譯指示文件中的資料流。|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS DE|代表 DE、 指定名稱和類別識別碼 (CLSID) 所提供的文件。|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE、 EE|代表偵錯文件的總和檢查碼，並可讓您傳遞元件之間的總和檢查碼。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS DE|代表文件內容，對應到特定的陳述式和程式碼內容的文件中的位置。|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS DE|表示文件內的一般位置。|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|表示原始程式檔中的字元位移位置。|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS DE|代表 DE 所提供的文字文件 (衍生自[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md))，提供的實際文字。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|若要指定記憶體中的原始程式檔的變更傳送 DE。|  
  
##  <a name="Events"></a> 事件  
 這些介面代表 DE 與工作階段的偵錯管理員 (SDM) 之間傳送的所有事件。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE 傳送以要求開啟的文件。|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|偵錯引擎 (DE) 過程中傳送此介面至工作階段的偵錯管理員 (SDM) 的狀態設列訊息符號載入。|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|中斷程式完成時傳送 DE。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|繫結中斷點時，由 DE 傳送。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|當中斷點無法繫結時，由 DE 傳送。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|在到達中斷點時，由 DE 傳送。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|解除繫結中斷點時，由 DE 傳送。|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|傳送 DE 以判斷是否應該停止的特定位置。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|若要指定記憶體中的原始程式檔的變更傳送 DE。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|表示已準備好處理偵錯工作傳送 DE 每個新執行個體。|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|代表正在偵錯的程式已準備好要執行的第一個指令傳送 DE。|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|介面，供其他事件的介面，這可能會傳回錯誤，用來提供人類看得懂的錯誤訊息。|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE、 PS|基底介面都衍生自其他所有事件的介面。|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|表示傳送事件 （以實作特定的事件介面的物件） 之 SDM 所實作的介面。|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|傳送 DE 時進行偵錯程式中發生例外狀況。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|完成非同步的運算式評估時，由 DE 傳送。|  
|IDebugFindSymbolEvent2||已過時。 請勿使用。|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|DE 攔截例外狀況處理完成時傳送。|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|DE 程式完成載入時傳送。|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|傳送到具有 IDE 顯示 DE 參考用訊息給使用者。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|載入或卸載模組時，由 DE 傳送。|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|訊號[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具 UI，警告使用者符號找不到啟動可執行檔。|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|傳送到具有 IDE 顯示 DE 的任意字串。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS DE|傳送埠與任何接聽程式通訊連接埠事件。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE、 PS|在建立處理序傳送 DE 或連接埠。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE、 PS|處理程序已被終結時傳送 DE 或連接埠。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE、 PS|在建立程式之後，由 DE 或連接埠傳送。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE、 PS|程式已被終結時傳送 DE 或連接埠。|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|可讓偵錯引擎，將覆寫預設行為[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 偵錯工作階段結束時。|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|程式的名稱變更時傳送的偵錯引擎 (DE) 從工作階段的偵錯管理員 (SDM)。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|傳送 DE 當新的屬性 (由`IDebugProperty2`介面) 已建立。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|DE 屬性已被終結時傳送。|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|不出的或進入函式，以便正確顯示的傳回值時，由 DE 傳送。|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|啟用偵錯引擎讀取度量設定從遠端。|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|DE 到、 不進入或超出指令的步驟完成時傳送。|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|傳送 DE 以指示成功或失敗的載入模組的符號。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|在建立執行緒時，由 DE 傳送。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|在終結執行緒時，由 DE 傳送。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|執行緒變更其名稱時，由 DE 傳送。|  
  
##  <a name="Expressions"></a>運算式  
 這些介面代表要在特定內容中評估運算式。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|表示要評估的運算式。 取自[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|代表用來評估運算式的內容。 取自[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|完成非同步的運算式評估時，由 DE 傳送。|  
  
##  <a name="Memory"></a>記憶體  
 這些介面代表記憶體中的位元組序列。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|代表可以讀取或寫入的記憶體中的位元組序列。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示在記憶體中的一連串的位元組的位置。|  
  
##  <a name="Modules"></a> 模組  
 這些介面代表一個模組，其對應的可執行檔或。DLL 的檔案。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|代表單一可執行檔或 DLL。|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|代表[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)支援符號。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|載入或卸載模組時，由 DE 傳送。|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|表示包含在 PDB 檔案中的來源伺服器資訊。|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|表示列舉類型之模組的已知誤[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)。|  
  
##  <a name="Ports"></a>連接埠  
 這些介面代表連接埠和通訊埠供應商。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS PS|代表本機電腦上的預設連接埠。|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|可讓偵錯引擎，使用 DCOM 詢問[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI，請確定防火牆會封鎖遠端偵錯。|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS PS|代表連接埠。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|傳送埠與任何接聽程式通訊連接埠事件。|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|表示可以啟動和終止處理程序的連接埠。|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|用來註冊及取消註冊程式與連接埠。可讓追蹤目前正在偵錯程式的連接埠。|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|代表自訂的 UI 中選取連接埠。|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|表示從中新的連接埠會建立或位於連接埠的要求。|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|表示連接埠的供應商。|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|代表可以保存的連接埠的供應商 （儲存到磁碟） 它所建立的連接埠相關資訊。|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|可讓[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]顯示文字內的 UI**傳輸資訊**區段**附加至處理序** 對話方塊。|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|可讓目標電腦的相關資訊的查詢。|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS PS|代表一組連接埠列舉型別。|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|代表一組連接埠供應商的列舉型別。|  
  
##  <a name="Processes"></a>處理程序  
 這些介面代表處理程序包含一或多個程式的單一可執行檔。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS、 DE|表示執行的電腦的處理序。|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS、 DE|表示正在支援的處理序偵錯 (用來取代步驟，繼續進行，並執行方法[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面)。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE、 PS|在建立處理序傳送 DE 或連接埠。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE、 PS|處理程序已被終結時傳送 DE 或連接埠。|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|表示必須追蹤哪個工作階段已附加至該處理序。|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|代表一組連接埠上的處理序的列舉。|  
  
##  <a name="Programs"></a>程式  
 這些介面代表邏輯單元不一定對應至實體的可執行檔或模組執行的程式。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|代表[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)需要與其他同時進行偵錯的程式正常運作。|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE、 PS|表示執行的邏輯單元。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE、 PS|在建立程式之後，由 DE 或連接埠傳送。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE、 PS|程式已被終結時傳送 DE 或連接埠。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE、 PS|代表[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) ，可以由多個偵錯引擎。|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|代表[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ，必須要能夠追蹤工作階段已附加至該。|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE、 PS|代表[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ，可以傳回正在執行的程序的相關資訊。|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE、 PS|代表可進行偵錯的程式。|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE、 PS|允許的嘗試附加至相關聯的程式通知程式節點。|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|提供方法來查詢有關受該 DE 程式 DE SDM。|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|使用 DEs 向 SDM，以顯示它們正在進行偵錯的程式。|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE、 PS|代表[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) ，可以跨封送處理介面執行緒或處理序界限。|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE、 PS|表示列舉類型的一組程式。|  
  
##  <a name="Properties"></a> 屬性  
 這些介面代表相關聯的特定內容，通常運算式評估的結果值的屬性。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|代表[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ，可以自訂方式來顯示其值。|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|代表堆疊框架、 文件，或運算式評估的結果值。|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|代表[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)支援任意長度的字串。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|傳送 DE 當新的屬性 (由[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面) 已建立。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|DE 屬性已被終結時傳送。|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|表示的屬性，可以存在於任何特定的堆疊框架以外的參考。|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|針對一組代表列舉[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構描述變數、 暫存器、 參數和運算式。|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|針對一組代表列舉[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。|  
  
##  <a name="StackFrames"></a>堆疊框架  
 這些介面代表堆疊框架，在內容中的中斷點或例外狀況發生。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示內容中的中斷點或例外狀況發生。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|代表[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)此運算子可以處理攔截例外狀況。|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|表示列舉類型的集合上[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)結構而指定的函式呼叫使用以達到特定的堆疊框架的順序。|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|針對一組代表列舉[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構描述的堆疊框架。|  
  
##  <a name="Threads"></a> 執行緒  
 這些介面代表執行緒和其相關聯的事件。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|表示執行的執行緒。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|在建立執行緒時，由 DE 傳送。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|在終結執行緒時，由 DE 傳送。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|執行緒變更其名稱時，由 DE 傳送。|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|代表一組執行緒列舉型別。|  
  
##  <a name="TypeVisualizers"></a>類型的視覺化檢視  
 這些介面會提供支援的類型視覺化檢視。 通常實作這些介面是由運算式評估工具。  
  
|介面|由實作|說明|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|表示要呈現給類型視覺化檢視的位元組陣列。|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|提供方法來取得要傳遞給類型視覺化檢視資料的存取權。|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|表示可存取的屬性[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)實作。|  
  
## <a name="see-also"></a>另請參閱  
 [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [建立自訂的偵錯引擎](../../../extensibility/debugger/creating-a-custom-debug-engine.md)