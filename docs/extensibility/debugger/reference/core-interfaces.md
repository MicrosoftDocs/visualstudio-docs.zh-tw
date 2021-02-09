---
title: 核心介面 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee2f44e5d75d44cfc1c903d462e7a1df360eeefa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899174"
---
# <a name="core-interfaces"></a>核心介面
下列介面是使用來擴充偵錯工具的核心介面 [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] 。

## <a name="discussion"></a>討論
 這些介面主要是用來建立 debug engine (DE) 。 這些是依類別組織：

- [[中斷點]](#Breakpoints)

- [內容](#Contexts)

- [核心伺服器](#CoreServer)

- [Debug 引擎](#DebugEngines)

- [文件](#Documents)

- [事件](#Events)

- [運算式](#Expressions)

- [記憶體](#Memory)

- [單元](#Modules)

- [連接埠](#Ports)

- [處理序](#Processes)

- [程式](#Programs)

- [屬性](#Properties)

- [堆疊框架](#StackFrames)

- [執行緒](#Threads)

- [型別視覺化](#TypeVisualizers)

  可以執行介面的實體如下：

- Debug Engine (DE) 

- 埠供應商 (PS) 

-  (EE) 的運算式評估工具

- Visual Studio (VS) 

## <a name="breakpoints"></a><a name="Breakpoints"></a> 中斷點
 這些介面與中斷點的執行和追蹤有關。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|表示系結至記憶體位置的中斷點。|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|當中斷點系結至記憶體位置時，由 DE 傳送。|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|代表中斷點要求的檔總和檢查碼。|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|當中斷點無法系結至記憶體位置時，就會由 DE 來傳送。|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|在到達中斷點時由 DE 傳送。|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|代表中斷點的要求;用於建立暫止中斷點。|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|代表中斷點的要求;用於建立暫止中斷點。|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|表示用來系結中斷點的資訊。|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|當中斷點從記憶體位置解除系結時，由 DE 傳送。|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|表示)  (傳回的無效中斷點 `IDebugBreakpointErrorEvent2` 。|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|表示無效中斷點的解析資訊。|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|代表函數中設定中斷點的位置。|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|代表要系結的中斷點;用於建立系結的中斷點。|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|表示一組系結中斷點的列舉。|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|表示在一組無法系結至記憶體位置的中斷點上的列舉。|

## <a name="contexts"></a><a name="Contexts"></a> 上下文
 這些介面代表正在進行程式設計的程式內各種類型的內容。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|表示程式碼指令的開始位置。|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|擴充 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 介面，以啟用模組和進程介面的抓取。|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS、DE|代表檔中的位置。|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示用來評估運算式的內容。|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示位元組集合之記憶體中的開始位置。|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|代表中斷點或例外狀況的堆疊框架內容。|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|代表中斷點或例外狀況的堆疊框架內容。|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|表示一組程式碼內容的列舉。|

## <a name="core-server"></a><a name="CoreServer"></a> 核心伺服器
 這些介面代表正在偵錯工具的電腦。 這些都是由執行， [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 但可由 debug 引擎來呼叫。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|提供對埠和埠供應商的存取，以及電腦的相關資訊。|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|表示支援遠端偵錯的 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 。|

## <a name="debug-engines"></a><a name="DebugEngines"></a> Debug 引擎
 這些介面代表調試引擎和其相關聯的事件。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|表示自訂的 debug engine。|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|表示支援載入符號、JustMyCode 和例外狀況的自訂偵錯工具引擎。|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|由 DE 的每個新實例傳送，表示它已經準備好處理偵錯工具。|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|表示支援啟動程式的自訂偵錯工具引擎。|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE、PS|表示處理多個 debug 引擎的程式節點。|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|提供一種方法，讓 SDM 從執行緒、程式或堆疊框架取得偵測引擎的介面。|

## <a name="documents"></a><a name="Documents"></a> 檔
 這些介面表示檔 (原始檔) 及其相關聯的專案。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|由 DE 傳送，要求要開啟的檔。|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|代表檔中拆解指令的資料流程。|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS、DE|表示由 DE 提供的檔，指定名稱和類別識別碼 (CLSID) 。|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE，EE|表示 debug 檔的總和檢查碼，並且可在元件之間傳遞總和檢查碼。|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS、DE|表示檔內容，這是檔中對應至特定語句和程式碼內容的位置。|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS、DE|代表檔內的一般位置。|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|以字元位移表示原始檔中的位置。|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS、DE|代表衍生自 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)) 的 DE (所提供的文字檔，並提供實際的文字。|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|由 DE 傳送，以指定記憶體中原始程式檔的變更。|

## <a name="events"></a><a name="Events"></a> 事件
 這些介面代表在 DE 和會話 debug manager (SDM) 之間傳送的所有事件。

| 介面 | 實作為 | Description |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | 由 DE 傳送，要求要開啟的檔。 |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Debug engine (DE) 會將這個介面傳送至會話 debug manager (SDM) ，在符號載入期間設定狀態列訊息。 |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | 當程式中的斷路器完成時傳送。 |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | 在系結中斷點時由 DE 傳送。 |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | 當中斷點無法系結時，由 DE 傳送。 |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | 在到達中斷點時由 DE 傳送。 |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | 當中斷點未系結時，由 DE 傳送。 |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | 由 DE 傳送，以判斷是否應該在特定位置停止。 |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | 由 DE 傳送，以指定記憶體中原始程式檔的變更。 |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | 由 DE 的每個新實例傳送，表示它已經準備好處理偵錯工具。 |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | 由 DE 傳送以表示正在進行調試的程式已準備好執行第一個指令。 |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | 其他事件介面所使用的介面，可能會傳回錯誤，以提供人們可讀取的錯誤訊息。 |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE、PS | 衍生所有其他事件介面的基底介面。 |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | 表示 SDM 所執行的介面，事件 (表示為執行特定事件介面的物件) 傳送。 |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | 在正在進行調試的程式中發生例外狀況時，由 DE 傳送。 |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | 在非同步運算式評估完成時，由 DE 傳送。 |
| IDebugFindSymbolEvent2 | | 已過時。 請勿使用。 |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | 在處理攔截的例外狀況時，由 DE 所傳送。 |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | 當程式完成載入時由 DE 傳送。 |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | 由 DE 傳送，讓 IDE 向使用者顯示告知性訊息。 |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | 在載入或卸載模組時由 DE 傳送。 |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | 通知 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 偵錯工具 UI 警告使用者，找不到已啟動可執行檔的符號。 |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | 由 DE 傳送，讓 IDE 顯示任一字元串。 |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS、DE | 由埠傳送以將埠事件傳達給任何接聽程式。 |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE、PS | 在建立進程時由 DE 或 port 傳送。 |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE、PS | 當進程終結時，由 DE 或 port 傳送。 |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE、PS | 當程式建立時由 DE 或 port 傳送。 |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE、PS | 當程式損毀時，由 DE 或 port 傳送。 |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]當您結束 debug 會話時，可讓 debug engine 覆寫 UI 的預設行為。 |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | 當程式的名稱變更時，從 debug engine 傳送 (DE) 至會話 debug manager (SDM) 。 |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | 在介面) 所表示的新屬性 (建立時，由 DE 傳送 `IDebugProperty2` 。 |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | 當屬性已終結時由 DE 傳送。 |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | 在跳出或移出函式時由 DE 傳送，因此可以正確地顯示傳回值。 |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | 啟用調試引擎以從遠端讀取計量設定。 |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | 當逐步執行、跳過或移出指令的完成時，會由 DE 來傳送。 |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | 由 DE 傳送以表示載入模組符號的成功或失敗。 |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | 在建立執行緒時由 DE 傳送。 |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | 當執行緒終結時由 DE 傳送。 |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | 當執行緒變更其名稱時由 DE 傳送。 |

## <a name="expressions"></a><a name="Expressions"></a> 運算式
 這些介面代表要在特定內容中評估的運算式。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|表示要評估的運算式。 從 [IDebugExpressionCoNtext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面取得。|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示評估運算式的內容。 從 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 介面取得。|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|在非同步運算式評估完成時，由 DE 傳送。|

## <a name="memory"></a><a name="Memory"></a> 記憶
 這些介面代表記憶體中的位元組序列。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|代表記憶體中可讀取或寫入的位元組序列。|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|代表位元組序列之記憶體中的位置。|

## <a name="modules"></a><a name="Modules"></a> 模組
 這些介面代表對應到可執行檔或的模組。DLL 檔。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|表示單一可執行檔或 DLL。|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|表示支援符號的 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 。|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|在載入或卸載模組時由 DE 傳送。|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|表示 PDB 檔案中包含的來源伺服器資訊。|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|代表 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)已知的一組模組的列舉。|

## <a name="ports"></a><a name="Ports"></a> 港口
 這些介面代表埠和埠供應商。

| 介面 | 實作為 | Description |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS、PS | 代表本機電腦上的預設通訊埠。 |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | 啟用使用 DCOM 的偵錯工具引擎，以要求 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 確定防火牆不會封鎖遠端偵錯程式。 |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS、PS | 表示埠。 |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | 由埠傳送以將埠事件傳達給任何接聽程式。 |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | 表示可以啟動和終止處理常式的埠。 |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | 用來透過埠註冊和取消註冊程式。允許埠追蹤目前正在進行調試的程式。 |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | 表示用來選取埠的自訂 UI。 |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | 代表將建立或找出新埠之埠的要求。 |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | 代表埠的供應商。 |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | 代表可保存 (儲存至磁片的埠供應商，) 它所建立之埠的相關資訊。 |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | 讓 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 在 [**附加至進程**] 對話方塊的 [**傳輸資訊**] 區段中顯示文字。 |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | 允許查詢目的電腦的相關資訊。 |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS、PS | 代表一組埠的列舉。 |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | 代表一組埠供應商的列舉。 |

## <a name="processes"></a><a name="Processes"></a> 過程
 這些介面代表進程，這是包含一個或多個程式的單一可執行檔。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS、DE|代表在電腦上執行的處理常式。|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS、DE|表示主動支援偵錯工具的進程， (用來取代 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面上的 Step、Continue 和 Execute 方法) 。|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE、PS|在建立進程時由 DE 或 port 傳送。|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE、PS|當進程終結時，由 DE 或 port 傳送。|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|表示必須追蹤哪些會話附加至該進程的進程。|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|表示埠上一組處理常式的列舉。|

## <a name="programs"></a><a name="Programs"></a> 程式
 這些介面代表程式、不一定會對應到實體可執行檔或模組的邏輯執行單位。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|代表需要與其他同時進行偵錯工具協同運作的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 。|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE、PS|表示執行的邏輯單元。|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE、PS|當程式建立時由 DE 或 port 傳送。|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE、PS|當程式損毀時，由 DE 或 port 傳送。|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE、PS|表示可由多個偵錯工具引擎處理的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 。|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|表示必須能夠追蹤附加至它的會話的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 。|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE、PS|表示可以傳回正在執行之進程相關資訊的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 。|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE、PS|表示可以進行調試的程式。|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE、PS|允許程式節點在嘗試附加至相關聯的程式時收到通知。|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|提供一種方法，讓 SDM 查詢 DE 所控制的程式。|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|DEs 用來向 SDM 註冊程式，以顯示正在進行調試的程式。|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE、PS|表示可以跨執行緒或進程界限封送處理介面的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 。|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE、PS|表示一組程式的列舉。|

## <a name="properties"></a><a name="Properties"></a> 屬性
 這些介面代表屬性，也就是與特定內容相關聯的值，通常是運算式評估的結果。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|表示可以自訂方式顯示其值的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 。|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|代表堆疊框架、檔或運算式評估結果的值。|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|表示支援任意長字串的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 。|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|當 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 介面所代表的新屬性 () 建立時，由 DE 傳送。|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|當屬性已終結時由 DE 傳送。|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|表示屬性的參考，該屬性可以存在於任何特定的堆疊框架之外。|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|表示一組 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 結構的列舉，其描述變數、暫存器、參數和運算式。|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|表示一組 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 結構上的列舉。|

## <a name="stack-frames"></a><a name="StackFrames"></a> 堆疊框架
 這些介面代表堆疊框架，也就是發生中斷點或例外狀況的內容。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示發生中斷點或例外狀況的內容。|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示可以處理攔截例外狀況的 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 。|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|表示在一組 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) 結構上的列舉，可指定用來到達特定堆疊框架的函式呼叫順序。|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|代表一組 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構的列舉，其描述堆疊框架。|

## <a name="threads"></a><a name="Threads"></a> 執行緒
 這些介面代表執行緒及其相關聯的事件。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|表示執行的執行緒。|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|在建立執行緒時由 DE 傳送。|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|當執行緒終結時由 DE 傳送。|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|當執行緒變更其名稱時由 DE 傳送。|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|表示一組執行緒的列舉。|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a> 型別視覺化
 這些介面可提供視覺化類型的支援。 這些介面通常是由運算式評估工具所執行。

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|表示要呈現給型別視覺化的位元組陣列。|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|提供方法，讓您取得要傳遞給型別視覺化程式之資料的存取權。|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|表示提供 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 執行存取權的屬性。|

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [建立自訂的偵錯引擎](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
