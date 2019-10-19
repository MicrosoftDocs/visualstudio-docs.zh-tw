---
title: 動態指令碼偵錯工具介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 477374d93e4d8d5139197dcd49fef0e930e5ff32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572697"
---
# <a name="active-script-debugger-interfaces"></a>動態指令碼偵錯工具的介面
Activdbg 和 activdbg100 標頭檔提供本節所列的介面、列舉和結構。 它們是用於偵錯工具腳本。  
  
> [!NOTE]
> @No__t_0 介面和 `IEnumJsStackFrames` 介面首次發行于 Internet Explorer 11 中，以使用腳本來進行機器碼的偵錯工具。 這些介面的標頭檔是 jscript9diag。  
  
## <a name="in-this-section"></a>本章節內容  
 下列介面允許非語言相關的主機中性調試：  
  
- [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
- [IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)  
  
- [IActiveScriptErrorDebug 介面](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
- [IActiveScriptErrorDebug110 介面](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
- [IActiveScriptSiteDebug 介面](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
- [IActiveScriptSiteDebug32 介面](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
- [IActiveScriptSiteDebugEx 介面](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
- [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
- [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)  
  
- [IApplicationDebuggerUI 介面](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
- [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)  
  
- [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md)  
  
- [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)  
  
- [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
- [IDebugApplicationNodeEvents 介面](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
- [IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)  
  
- [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
- [IDebugApplicationThreadEvents110 介面](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
- [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)  
  
- [IDebugAsyncOperationCallBack 介面](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
- [IDebugCodeContext 介面](../../winscript/reference/idebugcodecontext-interface.md)  
  
- [IDebugCookie 介面](../../winscript/reference/idebugcookie-interface.md)  
  
- [IDebugDocument 介面](../../winscript/reference/idebugdocument-interface.md)  
  
- [IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
- [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
- [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)  
  
- [IDebugDocumentInfo 介面](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
- [IDebugDocumentProvider 介面](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
- [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)  
  
- [IDebugDocumentTextAuthor 介面](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
- [IDebugDocumentTextEvents 介面](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
- [IDebugDocumentTextExternalAuthor 介面](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
- [IDebugExpression 介面](../../winscript/reference/idebugexpression-interface.md)  
  
- [IDebugExpressionCallBack 介面](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
- [IDebugExpressionContext 介面](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
- [IDebugFormatter 介面](../../winscript/reference/idebugformatter-interface.md)  
  
- [IDebugHelper 介面](../../winscript/reference/idebughelper-interface.md)  
  
- [IDebugSessionProvider 介面](../../winscript/reference/idebugsessionprovider-interface.md)  
  
- [IDebugSessionProviderEx 介面](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
- [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)  
  
- [IDebugStackFrameSniffer 介面](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
- [IDebugStackFrameSnifferEx 介面](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
- [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)  
  
- [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)  
  
- [IEnumDebugApplicationNodes 介面](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
- [IEnumDebugCodeContexts 介面](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
- [IEnumDebugExpressionContexts 介面](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
- [IEnumDebugStackFrames 介面](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
- [IEnumJsStackFrames 介面](../../winscript/reference/ienumjsstackframes-interface.md)  
  
- [IEnumRemoteDebugApplications 介面](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
- [IEnumRemoteDebugApplicationThreads 介面](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
- [IJsDebug 介面](../../winscript/reference/ijsdebug-interface.md)  
  
- [IJsDebugBreakPoint 介面](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
- [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
- [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)  
  
- [IJsDebugProcess 介面](../../winscript/reference/ijsdebugprocess-interface.md)  
  
- [IJsDebugProperty 介面](../../winscript/reference/ijsdebugproperty-interface.md)  
  
- [IJsDebugStackWalker 介面](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
- [IJsEnumDebugProperty 介面](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
- [IMachineDebugManager 介面](../../winscript/reference/imachinedebugmanager-interface.md)  
  
- [IMachineDebugManagerCookie 介面](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
- [IMachineDebugManagerEvents 介面](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
- [IProcessDebugManager 介面](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
- [IProvideExpressionContexts 介面](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
- [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)  
  
- [IRemoteDebugApplication110 介面](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
- [IRemoteDebugApplicationEx 介面](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
- [IRemoteDebugApplicationEvents 介面](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
- [IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
- [IRemoteDebugApplicationThreadEx 介面](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
- [ISetNextStatement 介面](../../winscript/reference/isetnextstatement-interface.md)  
  
- [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
- [IWebAppDiagnosticsSetup 介面](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
- [IWebAppDiagnosticsObjectInitialization 介面](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
  下一節列出用來進行偵錯工具的常數、列舉和結構：  
  
- [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯概觀](../../winscript/active-script-debugging-overview.md)