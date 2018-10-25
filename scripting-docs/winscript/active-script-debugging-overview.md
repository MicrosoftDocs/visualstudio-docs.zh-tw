---
title: 動態指令碼偵錯概觀 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447a8faf6e62448e7e8ce9ee8d7d8097fba2dd7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919360"
---
# <a name="active-script-debugging-overview"></a>動態指令碼偵錯概觀
動態指令碼偵錯介面允許進行非語言相關、非主機相關偵錯，並支援各種開發環境。  
  
 ![指令碼主機處理序](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
圖 1  
  
 非語言相關偵錯環境可以支援任何程式設計語言或混合使用程式設計語言，而不需要具有對其中任何語言的特定知識。 偵錯環境也支援跨語言逐步執行和中斷點  (本概觀主要著重於支援指令碼語言，例如 VBScript 和 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)])。  
  
 非主機相關偵錯工具可以自動與任何動態指令碼主機 (例如 Internet Explorer 或自訂主機) 搭配使用。 主機會控制偵錯工具向使用者顯示的內容，其中包含文件樹狀結構的結構、內容，以及偵錯文件的語法著色。 這可讓已偵錯的原始程式碼顯示在主機文件的內容中。 例如，Internet Explorer 可以在 HTML 頁面中顯示指令碼。  
  
 在下列各小節中，會討論主動式偵錯中的每個重要元件以及其相關聯的介面。 不過，更進一步之前，必須定義數個重要主動式偵錯概念：  
  
 Host Application - 主應用程式  
 裝載指令碼引擎並提供一組可編寫指令碼之物件 (或「物件模型」) 的應用程式。  
  
 語言引擎  
 一個元件，提供剖析、執行和偵錯特定語言的抽象概念。  
  
 偵錯工具 IDE  
 應用程式，透過與主應用程式和語言引擎進行通訊來提供偵錯 UI。  
  
 機器偵錯管理員  
 一個元件，維護可偵錯應用程式處理序的登錄。  
  
 處理序偵錯管理員  
 一個元件，維護特定應用程式的可偵錯文件樹狀結構、追蹤執行中執行緒等等。  
  
 文件內容  
 文件內容是代表主機文件原始程式碼中特定範圍的抽象概念。  
  
 程式碼內容  
 程式碼內容代表語言引擎之執行中程式碼中的特定位置 (「虛擬指令指標」)。  
  
 運算式內容  
 語言引擎可能在其中評估運算式的特定內容 (例如，堆疊框架)。  
  
 物件瀏覽  
 物件之名稱、類型、值和子物件的結構化語言無關表示法，適用於實作「監看式視窗」 UI。  
  
 以下概述每個重要主動式偵錯元件以及對應的相關聯介面，而且後面接著這些介面的詳細資料。  
  
## <a name="language-engine"></a>語言引擎  
 語言引擎提供：  
  
- 語言剖析和執行。  
  
- 偵錯支援 (中斷點等等)。  
  
- 運算式評估。  
  
- 語法著色。  
  
- 物件瀏覽。  
  
- 堆疊列舉和剖析。  
  
  以下是指令碼引擎所需的介面，支援提供偵錯、運算式評估和物件瀏覽。 主應用程式會使用這些介面來對應其文件內容與引擎程式碼內容，而偵錯工具 UI 也會使用它們來進行運算式評估、堆疊列舉和物件瀏覽。  
  
  [IActiveScriptDebug 介面](../winscript/reference/iactivescriptdebug-interface.md)  
  提供語法著色和程式碼內容列舉。  
  
  [IActiveScriptErrorDebug 介面](../winscript/reference/iactivescripterrordebug-interface.md)  
  傳回錯誤的文件內容和堆疊框架。  
  
  [IActiveScriptSiteDebug 介面](../winscript/reference/iactivescriptsitedebug-interface.md)  
  主機已提供從指令碼引擎到偵錯工具的連結。  
  
  [IDebugCodeContext 介面](../winscript/reference/idebugcodecontext-interface.md)  
  在執行緒中提供虛擬「指令指標」。  
  
  [IEnumDebugCodeContexts 介面](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  列舉對應至文件內容的程式碼內容。  
  
  [IDebugStackFrame 介面](../winscript/reference/idebugstackframe-interface.md)  
  代表執行緒堆疊上的邏輯堆疊框架。  
  
  [IDebugExpressionContext 介面](../winscript/reference/idebugexpressioncontext-interface.md)  
  提供可在其中評估運算式的內容。  
  
  [IDebugStackFrameSniffer 介面](../winscript/reference/idebugstackframesniffer-interface.md)  
  提供方法來列舉邏輯堆疊框架。  
  
  [IDebugExpression 介面](../winscript/reference/idebugexpression-interface.md)  
  代表非同步評估的運算式。  
  
  [IDebugSyncOperation 介面](../winscript/reference/idebugsyncoperation-interface.md)  
  可讓指令碼引擎抽取巢狀於特定已封鎖執行緒時需要執行的作業。  
  
  [IDebugAsyncOperation 介面](../winscript/reference/idebugasyncoperation-interface.md)  
  提供同步偵錯作業的非同步存取。  
  
  [IDebugAsyncOperationCallBack 介面](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  提供與 `IDebugAsyncOperation` 介面評估進度相關的狀態事件。  
  
  [IEnumDebugExpressionContexts 介面](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  列舉 `IDebugExpressionContexts` 物件的集合。  
  
  [IProvideExpressionContexts 介面](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  提供方法來列舉特定元件已知的運算式內容。  
  
  [IDebugFormatter 介面](../winscript/reference/idebugformatter-interface.md)  
  允許語言或 IDE 來自訂 VARIANT 值或 VARTYPE 類型與字串之間的轉換。  
  
  [IDebugStackFrameSnifferEx 介面](../winscript/reference/idebugstackframesnifferex-interface.md)  
  列舉 PDM 的邏輯堆疊框架。  
  
## <a name="hosts"></a>主機  
 主機：  
  
- 裝載語言引擎。  
  
- 提供物件模型 (可編寫指令碼的物件集)。  
  
- 定義可進行偵錯的文件樹狀結構和其內容。  
  
- 將指令碼組織成虛擬應用程式。  
  
  有兩種主機：  
  
- 無聲主機僅支援基本動態指令碼介面。 它無法控制文件結構或組織；這完全取決於提供給語言引擎的指令碼。  
  
- 智慧主機支援較大的一組介面，讓它可定義文件樹狀結構、文件內容和語法著色。 有一組協助程式介面 (如下列小節所述)，可讓主機更輕鬆地成為智慧主機。  
  
### <a name="smart-host-helper-interfaces"></a>智慧主機協助程式介面  
 `IDebugDocumentHelper` 方法提供一組大幅簡化的介面，讓主機可用來取得智慧裝載的優點，而不需要處理完整主機介面的完整複雜性和 (能力)。  
  
 當然，主機不需要使用這些介面。 不過，使用這些介面可以避免實作或使用一些更複雜的介面。  
  
 [IDebugDocumentHelper 介面](../winscript/reference/idebugdocumenthelper-interface.md)  
 由 PDM 所實作，並提供智慧裝載所需之許多介面的實作。  
  
 [IDebugDocumentHost 介面](../winscript/reference/idebugdocumenthost-interface.md)  
 已由主機 (選擇性) 實作，以向偵錯工具公開主機特定功能 (例如語法著色)。  
  
 如需詳細資訊，請參閱[實作智慧主機協助程式介面](../winscript/implementing-smart-host-helper-interfaces.md)。  
  
### <a name="full-smart-host-interfaces"></a>完整智慧主機介面  
 如果智慧主機未使用協助程式介面，則以下是智慧主機必須實作或使用的一組完整介面。  
  
 主機所實作的介面：  
  
 [IDebugDocumentInfo 介面](../winscript/reference/idebugdocumentinfo-interface.md)  
 提供或許未具現化之文件的相關資訊。  
  
 [IDebugDocumentProvider 介面](../winscript/reference/idebugdocumentprovider-interface.md)  
 提供方法，視需要來具現化文件。  
  
 [IDebugDocument 介面](../winscript/reference/idebugdocument-interface.md)  
 所有偵錯文件的基底介面。  
  
 [IDebugDocumentText 介面](../winscript/reference/idebugdocumenttext-interface.md)  
 存取純文字版的偵錯文件。  
  
 [IDebugDocumentTextAuthor 介面](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 允許編輯純文字版的偵錯文件。  
  
 [IDebugDocumentContext 介面](../winscript/reference/idebugdocumentcontext-interface.md)  
 提供所偵錯文件之部分的抽象表示法。  
  
 PDM 代表主機所實作的介面：  
  
 [IDebugApplicationNode 介面](../winscript/reference/idebugapplicationnode-interface.md)  
 提供專案樹狀結構內的內容，以擴充 `IDebugDocumentProvider` 介面的功能。  
  
## <a name="debugger-ide"></a>偵錯工具 IDE  
 IDE 是與語言無關的偵錯 UI。 它提供：  
  
- 文件檢視器/編輯器。  
  
- 中斷點管理。  
  
- 運算式評估和監看式視窗。  
  
- 堆疊框架瀏覽。  
  
- 物件/類別瀏覽。  
  
- 瀏覽虛擬應用程式結構。  
  
  偵錯工具所實作的介面：  
  
  [IApplicationDebugger 介面](../winscript/reference/iapplicationdebugger-interface.md)  
  偵錯工具 IDE 工作階段所公開的主要介面。  
  
  [IApplicationDebuggerUI 介面](../winscript/reference/iapplicationdebuggerui-interface.md)  
  讓外部元件進一步控制偵錯工具的使用者介面 (UI)。  
  
  [IDebugExpressionCallBack 介面](../winscript/reference/idebugexpressioncallback-interface.md)  
  提供 `IDebugExpression` 評估進度的狀態事件。  
  
  [IDebugDocumentTextEvents 介面](../winscript/reference/idebugdocumenttextevents-interface.md)  
  提供指出相關聯文字文件變更的事件。  
  
  [IDebugApplicationNodeEvents 介面](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  提供 `IDebugApplicationNode` 介面的事件介面。  
  
### <a name="machine-debug-manager"></a>機器偵錯管理員  
 機器偵錯管理員提供虛擬應用程式與偵錯工具之間的連結點，方法是維護和列舉使用中虛擬應用程式的清單。  
  
 [IDebugSessionProvider 介面](../winscript/reference/idebugsessionprovider-interface.md)  
 建立執行中應用程式的偵錯工作階段。  
  
 [IMachineDebugManager 介面](../winscript/reference/imachinedebugmanager-interface.md)  
 機器偵錯管理員的主要介面。  
  
 [IMachineDebugManagerCookie 介面](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 與 `IMachineDebugManager` 介面類似，但此介面支援偵錯 Cookie。  
  
 [IMachineDebugManagerEvents 介面](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 通知機器偵錯管理員所維護的執行中應用程式清單變更。  
  
 [IEnumRemoteDebugApplications 介面](../winscript/reference/ienumremotedebugapplications-interface.md)  
 列舉機器上的執行中應用程式。  
  
### <a name="process-debug-manager"></a>處理序偵錯管理員  
 PDM 執行下列作業：  
  
- 同步處理多個語言引擎的偵錯。  
  
- 維護可偵錯文件樹狀結構。  
  
- 合併堆疊框架。  
  
- 跨語言引擎協調中斷點和逐步執行。  
  
- 追蹤執行緒。  
  
- 維護非同步處理的偵錯工具執行緒。  
  
- 與機器偵錯管理員和偵錯工具 IDE 進行通訊。  
  
  以下是處理序偵錯管理員所提供的介面。  
  
  [IProcessDebugManager 介面](../winscript/reference/iprocessdebugmanager-interface.md)  
  處理序偵錯管理員的主要介面。 此介面可以建立、新增或移除處理序中的虛擬應用程式。  
  
  [IRemoteDebugApplication 介面](../winscript/reference/iremotedebugapplication-interface.md)  
  代表執行中應用程式。  
  
  [IDebugApplication 介面](../winscript/reference/idebugapplication-interface.md)  
  公開非遠端偵錯方法，以供語言引擎和主機使用。  
  
  [IRemoteDebugApplicationThread 介面](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  代表特定應用程式內執行的執行緒。  
  
  [IDebugApplicationThread 介面](../winscript/reference/idebugapplicationthread-interface.md)  
  允許語言引擎和主機提供執行緒同步處理，以及維護執行緒特定偵錯狀態資訊。  
  
  [IEnumRemoteDebugApplicationThreads 介面](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  列舉應用程式中的執行中執行緒。  
  
  [IDebugThreadCall 介面](../winscript/reference/idebugthreadcall-interface.md)  
  分派已封送處理的呼叫。  
  
  [IDebugApplicationNode 介面](../winscript/reference/idebugapplicationnode-interface.md)  
  維護階層中文件的位置。  
  
  [IEnumDebugApplicationNodes 介面](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  列舉與應用程式建立關聯之節點的子節點。  
  
  [IEnumDebugStackFrames 介面](../winscript/reference/ienumdebugstackframes-interface.md)  
  列舉對應至從引擎合併之執行緒的堆疊框架。  
  
  [IDebugCookie 介面](../winscript/reference/idebugcookie-interface.md)  
  允許在指令碼偵錯工具中設定偵錯 Cookie。  
  
  [IDebugHelper 介面](../winscript/reference/idebughelper-interface.md)  
  作為物件瀏覽器的 Factory 以及指令碼引擎的簡單連線點。  
  
  [ISimpleConnectionPoint 介面](../winscript/reference/isimpleconnectionpoint-interface.md)  
  針對指令碼引擎，提供一種簡單的方式來描述和列舉在特定連接點引發的事件。  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具介面](../winscript/reference/active-script-debugger-interfaces.md)