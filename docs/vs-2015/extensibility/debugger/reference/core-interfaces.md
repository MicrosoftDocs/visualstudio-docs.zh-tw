---
title: 核心介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ff260b8b54e3aff37b9cbceffaa1e4b3a374556
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49217733"
---
# <a name="core-interfaces"></a>核心介面
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

下列介面會擴充偵錯工具所使用的核心介面[!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)]。  
  
## <a name="discussion"></a>討論  
 這些介面主要用來建立偵錯引擎 (DE)。 它們被依以下類別：  
  
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
  
-   [類型視覺化檢視](#TypeVisualizers)  
  
 可以實作介面的實體是：  
  
-   偵錯引擎 (DE)  
  
-   連接埠提供者 (PS)  
  
-   運算式評估工具 (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a> 中斷點  
 有關這些介面實作] 和 [追蹤的中斷點。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|表示繫結至記憶體位置的中斷點。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|當中斷點繫結的記憶體位置傳送 DE。|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|表示中斷點要求的文件總和檢查碼。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|當中斷點無法繫結至記憶體位置時，由 DE 傳送。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|在到達中斷點時，由 DE 傳送。|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|表示中斷點; 的要求用來建立暫止中斷點。|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|表示中斷點; 的要求用來建立暫止中斷點。|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|表示用來繫結中斷點的資訊。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|傳送 DE 中斷點解除繫結時從記憶體位置。|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|表示無效的中斷點 (由`IDebugBreakpointErrorEvent2`)。|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|表示無效的中斷點解析資訊。|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|表示函式中已設定中斷點的位置。|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|表示要繫結; 的中斷點用來建立繫結的中斷點。|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|表示列舉類型的繫結中斷點集合。|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|代表一組可能未繫結至記憶體位置的中斷點列舉型別。|  
  
##  <a name="Contexts"></a> 內容  
 這些介面代表各種內正在偵錯之程式的內容。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|表示程式碼指示的開始位置。|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|擴充[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)介面，可讓模組和處理程序介面擷取。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS DE|表示文件中的位置。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示要在其中評估運算式的內容。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|代表記憶體位元組的集合中的起始位置。|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示在中斷點或例外狀況的堆疊框架內容。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示在中斷點或例外狀況的堆疊框架內容。|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|代表一組程式碼內容的列舉型別。|  
  
##  <a name="CoreServer"></a> 核心伺服器  
 這些介面代表一個程式正在偵錯的電腦。 藉由實作這些[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]但可以呼叫到偵錯引擎。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|提供存取權的連接埠和連接埠提供者，以及電腦的相關資訊。|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|代表[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) ，支援遠端偵錯。|  
  
##  <a name="DebugEngines"></a> 偵錯引擎  
 這些介面代表偵錯引擎和其相關聯的事件。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|表示自訂的偵錯引擎。|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|表示支援的符號、 JustMyCode 和例外狀況的載入自訂的偵錯引擎。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|傳送每個 DE 的新執行個體指出它已準備好處理偵錯工作。|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|表示支援啟動程式的自訂偵錯引擎。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE PS|代表會處理多個偵錯引擎的程式節點。|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|提供了 SDM 取自介面來偵錯引擎的執行緒、 程式或堆疊框架的方式。|  
  
##  <a name="Documents"></a> 文件  
 這些介面代表文件 （來源檔案） 和其相關聯的項目。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE 傳送以要求開啟的文件。|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|表示從文件的反組譯指令資料流。|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS DE|代表 DE，指定名稱和類別識別碼 (CLSID) 所提供的文件。|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE EE|表示偵錯文件的總和檢查碼，並讓傳遞元件之間的總和檢查碼。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS DE|表示文件內容，對應至特定的陳述式和程式碼內容的文件內的位置。|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS DE|表示文件內的一般位置。|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|表示原始程式檔中的字元位移的位置。|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS DE|代表 DE 所提供的文字文件 (衍生自[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md))，提供實際的文字。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|若要指定記憶體中的原始程式檔的變更傳送 DE。|  
  
##  <a name="Events"></a> 事件  
 這些介面代表 DE 與工作階段的偵錯管理員 (SDM) 之間傳送的所有事件。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE 傳送以要求開啟的文件。|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) 的狀態設定，訊息列符號載入期間，傳送這個介面。|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|DE 中斷程式完成時傳送。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|當中斷點繫結傳送 DE。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|當中斷點無法繫結時，由 DE 傳送。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|在到達中斷點時，由 DE 傳送。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|解除繫結中斷點時，由 DE 傳送。|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|若要判斷其是否應在特定位置停止傳送 DE。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|若要指定記憶體中的原始程式檔的變更傳送 DE。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|傳送每個 DE 的新執行個體指出它已準備好處理偵錯工作。|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|代表正在偵錯程式已準備好要執行的第一個指令傳送 DE。|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|介面，可由其他事件的介面，這可能會傳回錯誤，以提供人類看得懂的錯誤訊息。|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE PS|基底介面都衍生自其他所有事件的介面。|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|表示事件 （表示為實作特定的事件介面的物件） 傳送以 SDM 所實作的介面。|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|正在進行偵錯的程式中發生例外狀況時傳送 DE。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|DE 非同步運算式評估完成時傳送。|  
|IDebugFindSymbolEvent2||已過時。 請勿使用。|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|DE 攔截例外狀況的處理完成時傳送。|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|程式已完成載入時，由 DE 傳送。|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|傳送至 IDE 顯示 DE 參考用訊息給使用者。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|載入或卸載模組時，由 DE 傳送。|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|訊號[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]偵錯工具 UI 來警告使用者符號找不到啟動可執行檔。|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|傳送至 IDE 顯示 DE 的任意字串。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS DE|傳送埠進行通訊的任何接聽程式連接埠事件。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE PS|在建立程序時，由 DE 或連接埠傳送。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE PS|處理程序已被終結時傳送 DE 或連接埠。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE PS|在建立程式時，由 DE 或連接埠傳送。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE PS|程式已被終結時傳送 DE 或連接埠。|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|可讓偵錯引擎覆寫預設行為[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]UI 時結束偵錯工作階段。|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|程式的名稱變更時傳送從偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM)。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|傳送 DE 時新的屬性 (由`IDebugProperty2`介面) 已建立。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|DE 屬性已被終結時傳送。|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|逐步出或函式，因此可以正確顯示的傳回值時，由 DE 傳送。|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|啟用偵錯引擎讀取計量設定從遠端。|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|已完成的步驟，透過，進出指令時，由 DE 傳送。|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|DE 傳送以指出成功或失敗的載入模組的符號。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|在建立執行緒時，由 DE 傳送。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|執行緒已被終結時傳送 DE。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|當執行緒變更其名稱時，由 DE 傳送。|  
  
##  <a name="Expressions"></a> 運算式  
 這些介面代表在特定內容中評估的運算式。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|表示要評估的運算式。 取自[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示用來評估運算式的內容。 取自[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|DE 非同步運算式評估完成時傳送。|  
  
##  <a name="Memory"></a> 記憶體  
 這些介面代表記憶體中的位元組的序列。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|代表可讀取或寫入的記憶體中的位元組序列。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示在記憶體中的一連串的位元組的位置。|  
  
##  <a name="Modules"></a> 模組  
 這些介面代表一個模組，可對應至可執行檔或。DLL 檔案。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|代表單一可執行檔或 DLL。|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|代表[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)支援符號。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|載入或卸載模組時，由 DE 傳送。|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|表示包含在 PDB 檔案中的來源伺服器資訊。|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|代表一組已知的模組列舉型別[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)。|  
  
##  <a name="Ports"></a> 連接埠  
 這些介面代表連接埠和連接埠提供者。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS PS|代表本機電腦上的預設連接埠。|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|可讓要求則會使用 DCOM 的偵錯引擎[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]UI，請確定防火牆會封鎖遠端偵錯。|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS PS|表示連接埠。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|傳送埠進行通訊的任何接聽程式連接埠事件。|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|表示可以啟動和終止處理序的連接埠。|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|用來註冊和取消註冊程式與連接埠;可讓以追蹤目前正在偵錯程式的連接埠。|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|代表自訂的 UI 中選取連接埠。|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|表示從其新的連接埠會建立或位於連接埠的要求。|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|表示連接埠的供應商。|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|表示可以保存的連接埠的供應商 （儲存至磁碟） 它所建立的連接埠相關資訊。|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|可讓[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]UI，以顯示內部文字**傳輸資訊**一節**附加至處理序** 對話方塊。|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|可讓目標電腦的相關資訊的查詢。|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS PS|列舉型別代表一組連接埠。|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|代表一組連接埠提供者的列舉型別。|  
  
##  <a name="Processes"></a> 處理程序  
 這些介面代表處理程序，包含一或多個程式的單一可執行檔。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS，DE|表示執行的電腦的處理序。|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS，DE|代表積極支援程序偵錯 (用來取代步驟，繼續執行，和執行方法[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面)。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE PS|在建立程序時，由 DE 或連接埠傳送。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE PS|處理程序已被終結時傳送 DE 或連接埠。|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|表示必須追蹤哪些工作階段已附加的處理程序。|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|表示一組連接埠上的處理序的列舉。|  
  
##  <a name="Programs"></a> 程式  
 這些介面代表程式，這不一定對應到實體的可執行檔或模組執行的邏輯單元。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|代表[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)需要同時進行偵錯其他程式正常運作。|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE PS|表示執行的邏輯單元。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE PS|在建立程式時，由 DE 或連接埠傳送。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE PS|程式已被終結時傳送 DE 或連接埠。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE PS|代表[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) ，可由多個偵錯引擎。|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|代表[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ，必須要能夠追蹤工作階段已附加。|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE PS|代表[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ，可以傳回正在執行的程序的相關資訊。|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE PS|表示可以進行偵錯的程式。|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE PS|允許程式節點，嘗試附加至相關聯的程式的通知。|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|可查詢該 DE 所控制的程式的相關規定了 SDM 讓。|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|使用 DEs 來向 SDM 顯示他們正在進行偵錯的程式。|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE PS|代表[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) ，可以跨封送處理介面執行緒或處理序界限。|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE PS|代表一組程式列舉。|  
  
##  <a name="Properties"></a> 屬性  
 這些介面代表屬性，與特定的內容，通常的運算式評估結果相關聯的值。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|代表[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)可以以自訂方式來顯示它的值。|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|代表堆疊框架、 文件或運算式評估的結果值。|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|代表[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)支援任意長度的字串。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|傳送 DE 時新的屬性 (由[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面) 已建立。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|DE 屬性已被終結時傳送。|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|表示可以存在於任何特定的堆疊框架以外的屬性參考。|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|透過一組代表列舉[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構會描述變數、 暫存器、 參數和運算式。|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|透過一組代表列舉[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。|  
  
##  <a name="StackFrames"></a> 堆疊框架  
 這些介面代表堆疊框架，在內容中的中斷點或例外狀況發生。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示內容中的中斷點或例外狀況發生。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|代表[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)此運算子可以處理攔截例外狀況。|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|透過一組代表列舉[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)結構而指定的函式呼叫來達到特定的堆疊框架的順序。|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|透過一組代表列舉[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構描述的堆疊框架。|  
  
##  <a name="Threads"></a> 執行緒  
 這些介面代表執行緒和其相關聯的事件。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|表示執行的執行緒。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|在建立執行緒時，由 DE 傳送。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|執行緒已被終結時傳送 DE。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|當執行緒變更其名稱時，由 DE 傳送。|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|代表一組執行緒列舉型別。|  
  
##  <a name="TypeVisualizers"></a> 類型視覺化檢視  
 這些介面類型視覺化檢視提供支援。 這些介面通常是由運算式評估工具實作。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|表示要呈現給類型視覺化檢視的位元組陣列。|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|提供方法來取得要傳遞至類型視覺化檢視資料的存取權。|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|代表屬性，提供存取權[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)實作。|  
  
## <a name="see-also"></a>另請參閱  
 [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [建立自訂的偵錯引擎](../../../extensibility/debugger/creating-a-custom-debug-engine.md)

