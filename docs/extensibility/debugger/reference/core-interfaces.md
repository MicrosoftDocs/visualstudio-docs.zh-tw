---
title: 核心介面 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737587"
---
# <a name="core-interfaces"></a>核心介面
以下介面是使用 延伸除錯器的核心[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]介面 。

## <a name="discussion"></a>討論區
 這些介面主要用於創建調試引擎 (DE)。 它們按類別組織在這裡:

- [斷點](#Breakpoints)

- [內容](#Contexts)

- [核心伺服器](#CoreServer)

- [偵錯引擎](#DebugEngines)

- [文件](#Documents)

- [事件](#Events)

- [運算式](#Expressions)

- [記憶體](#Memory)

- [模組](#Modules)

- [連接埠](#Ports)

- [過程](#Processes)

- [Programs](#Programs)

- [屬性](#Properties)

- [堆疊框架](#StackFrames)

- [執行緒](#Threads)

- [類型視覺化器](#TypeVisualizers)

  可以實現介面的實體是:

- 除錯引擎 (DE)

- 港口供應商 (PS)

- 運算式賦值器 (EE)

- 視覺工作室 (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>斷點
 這些介面與斷點的實現和跟蹤相關。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|表示綁定到記憶體位置的斷點。|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|當斷點綁定到記憶體位置時,DE 發送。|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|表示斷點請求的文檔校驗和。|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|當斷點無法綁定到記憶體位置時,DE 發送。|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|到達斷點時由 DE 發送。|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|表示斷點請求;用於創建掛起的斷點。|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|表示斷點請求;用於創建掛起的斷點。|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|表示用於綁定斷點的資訊。|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|當斷點從記憶體位置取消綁定時,DE 發送。|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|表示無效的斷點(由`IDebugBreakpointErrorEvent2`返回)。|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|表示有關無效斷點的解析資訊。|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|表示設置斷點的函數中的位置。|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|表示要綁定的斷點;用於創建綁定斷點。|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|表示對一組綁定斷點的枚舉。|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|表示對一組無法綁定到記憶體位置的斷點進行枚舉。|

## <a name="contexts"></a><a name="Contexts"></a>內容
 這些介面表示正在調試的程式中的各種上下文。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|表示代碼指令的起始位置。|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|擴展[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)介面,以便檢索模組和進程介面。|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, 德|表示文檔中的位置。|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示在其中計算表達式的上下文。|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示位元組集合記憶體中的起始位置。|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示斷點或異常處的堆疊幀上下文。|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示斷點或異常處的堆疊幀上下文。|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|表示對一組代碼上下文的枚舉。|

## <a name="core-server"></a><a name="CoreServer"></a>核心伺服器
 這些介面表示正在調試程序的計算機。 這些由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]調試引擎實現,但可以通過調試引擎調用。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|提供對埠和埠供應商的訪問以及有關計算機的資訊。|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|表示支援遠端調試的[IDebugCoreServer2。](../../../extensibility/debugger/reference/idebugcoreserver2.md)|

## <a name="debug-engines"></a><a name="DebugEngines"></a>偵錯引擎
 這些介面表示調試引擎及其關聯的事件。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|表示自定義調試引擎。|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|表示支援載入符號、JustMyCode 和異常的自定義調試引擎。|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|DE 的每個新實例發送,以指示它已準備好處理調試任務。|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|表示支援啟動程式的自定義調試引擎。|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|表示處理多個調試引擎的程式節點。|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|為 SDM 提供了一種從線程、程式或堆疊幀獲取調試引擎介面的方法。|

## <a name="documents"></a><a name="Documents"></a>檔案
 這些介面表示文檔(源檔)及其關聯元素。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE 發送以請求打開文檔。|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|表示文檔中拆解的說明流。|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, 德|表示 DE 提供的文件,指定名稱和類 ID (CLSID)。|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|表示調試文件的校驗和,並啟用在元件之間傳遞校驗和。|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, 德|表示文檔上下文,即文件中對應於特定語句和代碼上下文的位置。|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, 德|表示文檔中的一般位置。|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|將源檔中的位置表示為字元偏移量。|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, 德|表示 DE 提供的文字文件(派生自[IDebugDocument2),](../../../extensibility/debugger/reference/idebugdocument2.md)提供實際文本。|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|DE 發送以指定對記憶體中的源檔的更改。|

## <a name="events"></a><a name="Events"></a>事件
 這些介面表示 DE 和工作階段調試管理員 (SDM) 之間發送的所有事件。

| 介面 | 實施者 | 描述 |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | DE 發送以請求打開文檔。 |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | 除錯引擎 (DE) 將此介面傳送到工作階段除錯管理員 (SDM), 以在符號載入期間設定狀態列訊息。 |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | 當程式中斷完成後,DE 發送。 |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | 綁定斷點時由 DE 發送。 |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | 當斷點未綁定時,DE 發送。 |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | 到達斷點時由 DE 發送。 |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | 當斷點未綁定時由 DE 發送。 |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | DE 發送以確定是否應在特定位置停止。 |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | DE 發送以指定對記憶體中的源檔的更改。 |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | DE 的每個新實例發送,以指示它已準備好處理調試任務。 |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | DE 發送以指示正在調試的程式已準備好執行第一個指令。 |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | 其他事件介面使用的介面(可能會返回錯誤)來提供人類可讀的錯誤消息。 |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | 從中派生所有其他事件介面的基本介面。 |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | 表示 SDM 實現的介面,其中事件(表示為實現特定事件介面的物件)發送。 |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | 當正在調試的程式中出現異常時,DE 發送。 |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | 當非同步表達式計算完成時由 DE 發送。 |
| IDebugFind符號事件2 | | 已過時。 請勿使用。 |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | DE 在處理截獲的異常時發送。 |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | 當程式完成載入時由 DE 發送。 |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | DE 發送給 IDE 向使用者顯示資訊性消息。 |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | 當模組載入或卸載時由 DE 發送。 |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | 向[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]調試器 UI 發出訊號,警告使用者無法為啟動的可執行檔找到符號。 |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | DE 發送以讓 IDE 顯示任意字串。 |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, 德 | 由埠發送,用於將埠事件傳達給任何偵聽器。 |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | 創建行程時由 DE 或埠發送。 |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | 程序被銷毀時由 DE 或埠發送。 |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | 創建程式時由 DE 或埠發送。 |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | 程式或埠在程式被銷毀時發送。 |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | 使調試引擎在結束調試會話時覆蓋[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 的默認行為。 |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | 當程式名稱更改時,從除錯引擎 (DE) 傳送到工作階段除錯管理員 (SDM)。 |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | 創建新屬性(由`IDebugProperty2`介面表示)時由 DE 發送。 |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | 當屬性被銷毀時由 DE 發送。 |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | DE 在退出或超過函數時發送,以便可以正確顯示返回值。 |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | 使調試引擎能夠遠程讀取指標設置。 |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | 當進入、結束或退出指令時,DE 發送。 |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | DE 發送以指示模組載入符號的成敗。 |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | 建立線程時由 DE 發送。 |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | 當線程被銷毀時由 DE 發送。 |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | 當線程更改其名稱時由 DE 發送。 |

## <a name="expressions"></a><a name="Expressions"></a> 運算式
 這些介面表示要在特定上下文中計算的運算式。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|表示要計算的表達式。 從[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面獲取。|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示計算表達式的上下文。 從[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面獲取。|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|當非同步表達式計算完成時由 DE 發送。|

## <a name="memory"></a><a name="Memory"></a>記憶
 這些介面表示記憶體中的位元組序列。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|表示記憶體中可以從中讀取或寫入的位元組序列。|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示位元組序列的記憶體中的位置。|

## <a name="modules"></a><a name="Modules"></a>模組
 這些介面表示一個模組,它對應於可執行檔或 。DLL 檔。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|表示單個可執行檔或 DLL。|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|表示支援符號的[IDebugModule2。](../../../extensibility/debugger/reference/idebugmodule2.md)|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|當模組載入或卸載時由 DE 發送。|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|表示 PDB 檔中的源伺服器資訊。|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|表示[對 IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)已知的一組模組的枚舉。|

## <a name="ports"></a><a name="Ports"></a>港口
 這些介面表示埠和埠供應商。

| 介面 | 實施者 | 描述 |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | 表示本地電腦上的預設埠。 |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | 啟用使用 DCOM 要求[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 確保防火牆不會阻止遠端除錯的調試引擎。 |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | 表示埠。 |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | 由埠發送,用於將埠事件傳達給任何偵聽器。 |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | 表示可以啟動和終止進程的埠。 |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | 用於在埠註冊和取消註冊程式;允許埠跟蹤當前正在調試的程式。 |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | 表示用於選擇埠的自定義 UI。 |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | 表示將創建或定位新埠的埠的請求。 |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | 表示埠供應商。 |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | 表示可以保留(保存到磁碟)有關其創建的埠的資訊的埠供應商。 |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | 使[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 能夠在 **「附加到流程」** 對話框的 **「傳輸資訊**」部分內顯示文本。 |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | 允許查詢有關目標計算機的資訊。 |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | 表示對一組埠的枚舉。 |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | 表示對一組埠供應商的枚舉。 |

## <a name="processes"></a><a name="Processes"></a>過程
 這些介面表示進程,一個包含一個或多個程式的可執行檔。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|表示在電腦上運行的進程。|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|表示積極支援調試的進程(用於替換[IDebug Program2](../../../extensibility/debugger/reference/idebugprogram2.md)介面上的步驟、繼續和執行方法)。|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|創建行程時由 DE 或埠發送。|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|程序被銷毀時由 DE 或埠發送。|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|表示必須跟蹤附加到哪個作業階段的進程。|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|表示埠上一組進程的枚舉。|

## <a name="programs"></a><a name="Programs"></a>程式
 這些介面表示程式,邏輯執行單元不一定對應於物理可執行檔或模組。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|表示[IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md)它需要與同時調試的其他程序協同工作。|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|表示邏輯執行單元。|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|創建程式時由 DE 或埠發送。|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|程式或埠在程式被銷毀時發送。|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|表示一個[IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md)可以由多個調試引擎處理。|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|表示[IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md)它必須能夠追蹤附加到它的作業階段。|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|表示[IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md)它可以返回有關其運行過程的資訊。|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|表示可以調試的程式。|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|允許通知程式節點嘗試附加到關聯的程式。|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|為 SDM 提供了一種查詢 DE 有關該 DE 控制的程式的方法。|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|DEs 使用 SDM 註冊程式以顯示正在調試程式。|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|表示[IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md)它可以跨線程或進程邊界封送介面。|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|表示一組程式的枚舉。|

## <a name="properties"></a><a name="Properties"></a> 屬性
 這些介面表示屬性,與特定上下文關聯的值,通常是表達式計算的結果。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|表示[IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md)它可以通過自訂方式顯示其值。|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|表示堆疊幀、文檔或表達式計算的結果的值。|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|表示支援任意長字串的[IDebugProperty2。](../../../extensibility/debugger/reference/idebugproperty2.md)|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|創建新屬性(由[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面表示)時由DE發送。|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|當屬性被銷毀時由 DE 發送。|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|表示對可以存在於任何特定堆疊幀之外的屬性的引用。|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|表示對一組描述變數、寄存器、參數和運算式[的DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構的枚舉。|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|表示對一組[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構的枚舉。|

## <a name="stack-frames"></a><a name="StackFrames"></a>堆疊幀
 這些介面表示堆疊幀,其中發生了斷點或異常。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示發生斷點或異常的上下文。|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示[IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md)可以處理截獲的異常。|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|表示對[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)結構集的枚舉,這些結構指定用於到達特定堆疊幀的函數調用序列。|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|表示對一組[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構的枚舉,這些結構描述堆疊幀。|

## <a name="threads"></a><a name="Threads"></a>執行緒
 這些介面表示線程及其關聯事件。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|表示執行線程。|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|建立線程時由 DE 發送。|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|當線程被銷毀時由 DE 發送。|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|當線程更改其名稱時由 DE 發送。|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|表示對一組線程的枚舉。|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>類型視覺化器
 這些介面支援類型可視化器。 這些介面通常由表達式賦值器實現。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|表示要呈現給類型可視化工具的位元組。|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|提供了用於訪問要傳遞給類型可視化工具的數據的方法。|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|表示提供對[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)實現的訪問的屬性。|

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [建立自訂的偵錯引擎](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
