---
title: 偵錯節點屬性、選項頁
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0556dd29e37f45b460e3dde271384e94b1c09ed
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31951774"
---
# <a name="options-page-debugging-node-properties"></a>偵錯節點屬性、選項頁
下表描述與 [選項] 對話方塊的 [偵錯] 分類 `DTE.Properties("Debugging", <Property Page>)` 相關聯的頁面 (或屬性集合)。

## <a name="general"></a>一般
 `DTE.Properties("Debugging", "General")`

|屬性項目名稱|值|描述|
|------------------------|-----------|-----------------|
|PromptOnBreakpointDelete|Get/Set (布林值)|判斷偵錯工具是否先提示權限，再刪除專案中的所有中斷點。|
|BreakAllProcesses|Get/Set (布林值)|決定是否只要單一處理序中斷，偵錯工具即中斷所有處理序。|
|BreakAtBoundaries|Get/Set (布林值)|決定當 AppDomain 之間或 Managed 和原生程式碼之間發生越界的例外狀況時，偵錯工具是否中斷執行。|
|EnableAddressLevelDebugging|Get/Set (布林值)|決定是否啟用位址層級偵錯功能。|
|ShowDisassemblyIfNoSource|Get/Set (布林值)|決定無原始程式碼可用時，偵錯工具是否顯示反組譯碼。|
|EnableBreakpointFilters|Get/Set (布林值)|決定是否啟用中斷點篩選。|
|EnableExceptionAssistant|Get/Set (布林值)|決定例外狀況助理是否用於處理 Managed 例外狀況。|
|UnwindCallstack|Get/Set (布林值)|決定偵錯工具是否針對未處理的例外狀況回溯呼叫堆疊。|
|EnableJustMyCode|Get/Set (布林值)|決定 C# 和 Visual Basic 程式碼是否啟用 Just My Code。|
|ShowAllMembers|Get/Set (布林值)|決定偵錯工具是否針對非使用者物件，在 [變數] 視窗中顯示所有物件成員。 除非啟用 Just My Code，否則此選項沒有任何作用。|
|WarnIfNoUserCode|Get/Set (布林值)|決定當使用者嘗試附加至沒有使用者程式碼的處理程序時，偵錯工具是否發出警告。 除非啟用 Just My Code，否則此選項沒有任何作用。|
|EnablePropertyEvaluation|Get/Set (布林值)|決定偵錯工具是否自動評估 Managed 程式碼中的屬性和隱含函式呼叫。|
|CallStringConversion|Get/Set (布林值)|決定偵錯工具是否對 [變數] 視窗中的物件隱含呼叫字串轉換函式。|
|EnableSourceServer|Get/Set (布林值)|決定偵錯工具是否可存取來源伺服器的程式碼。|
|PrintSourceServerDiagnostics|Get/Set (布林值)|決定 [輸出] 視窗是否顯示與來源伺服器相關的診斷訊息。 除非啟用來源伺服器存取，否則此選項沒有任何作用。|
|HighlightEntireLine|Get/Set (布林值)|決定偵錯工具是否反白顯示中斷點整行和目前的陳述式。|
|RequireSourceToMatch|Get/Set (布林值)|決定開啟檔案進行偵錯時，偵錯工具是否需要來源檔案必須完全符合原始版本。|
|RedirectOutputToImmediate|Get/Set (布林值)|決定 [輸出] 視窗的輸出是否會重新導向至 [即時運算] 視窗。|
|ShowRawVariableStructure|Get/Set (布林值)|決定 [變數] 視窗中的物件是否以未經處理的格式顯示。|
|SuppressJitOptimization|Get/Set (布林值)|決定偵錯工具是否針對 Managed 程式碼隱藏 Just-In-Time 最佳化。|
|WarnIfNoSymbols|Get/Set (布林值)|如果啟動處理序時沒有偵錯符號可用，決定偵錯工具是否顯示警告。|
|WarnIfScriptDisabled|Get/Set (布林值)|如果啟動處理序時未啟用指令碼偵錯，決定偵錯工具是否顯示警告。|
|ShowMarkersForAllThreads|Get/Set (布林值)|決定偵錯工具是否顯示執行緒標記。|
|StepOverPropertiesAndOperators|Get/Set (布林值)|指定是否僅逐程序執行 Managed 程式碼中的屬性及運算子。|

## <a name="edit-and-continue"></a>編輯後繼續
 `DTE.Properties("Debugging", "EditAndContinue")`

|屬性項目名稱|值|描述|
|------------------------|-----------|-----------------|
|EnableEditAndContinue|Get/Set (布林值)|決定是否啟用 [編輯後繼續]。 此選項適用於所有支援 [編輯後繼續] 的語言。|
|InvokedByCommands|Get/Set (布林值)|當使用者選取 [步驟] 或 [繼續] 等偵錯命令時，決定 [編輯後繼續] 是否自動套用程式碼變更。 此選項僅適用於原生程式碼。|
|InvokedByCommandsAskFirst|Get/Set (布林值)|當使用者選取 [步驟] 或 [繼續] 等偵錯命令時，決定 [編輯後繼續] 是否提示使用者提供權限以套用程式碼變更。 此選項僅適用於原生程式碼。|
|WarnAboutStaleCode|Get/Set (布林值)|當 [編輯後繼續] 導致過期或過時的程式碼執行時，決定偵錯工具是否發出警告訊息。 此選項僅適用於原生程式碼。|
|RelinkChangesOnStop|Get/Set (短整數)|當應用程式停止執行時，決定 Visual Studio 是否重新連結 [編輯後繼續] 套用的程式碼變更。 此選項僅適用於原生程式碼。|
|AllowPrecompiling|Get/Set (短整數)|決定是否允許 [編輯後繼續] 在背景中載入先行編譯標頭檔。 此選項僅適用於原生程式碼。|

## <a name="just-in-time"></a>Just-In-Time
 `DTE.Properties("Debugging", "JustInTime")`

|屬性項目名稱|值|描述|
|------------------------|-----------|-----------------|
|JitManaged|Get/Set (布林值)|決定 Managed 程式碼是否啟用 Just-In-Time 偵錯。|
|JitNative|Get/Set (布林值)|決定原生程式碼是否啟用 Just-In-Time 偵錯。|
|JitScript|Get/Set (布林值)|決定指令碼程式碼是否啟用 Just-In-Time 偵錯。|

## <a name="native"></a>原生
 `DTE.Properties("Debugging", "Native")`

|屬性項目名稱|值|描述|
|------------------------|-----------|-----------------|
|LoadDllExports|Get/Set (布林值)|決定偵錯工具是否載入 DLL 匯出表。|
|EnableRPC|Get/Set (布林值)|決定偵錯工具是否可以逐步執行至 COM 遠端程序呼叫。|

## <a name="see-also"></a>請參閱

- [控制選項設定](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [在選項頁中決定屬性項目的名稱](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [字型和色彩節點屬性、選項頁面](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [文字編輯器節點屬性、選項頁面](../../ide/reference/options-page-text-editor-node-properties.md)
- [選項對話方塊、偵錯、一般](../../debugger/general-debugging-options-dialog-box.md)
- [選項對話方塊、偵錯、編輯後繼續](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)
- [選項對話方塊、偵錯、Just-In-Time](../../debugger/just-in-time-debugging-options-dialog-box.md)