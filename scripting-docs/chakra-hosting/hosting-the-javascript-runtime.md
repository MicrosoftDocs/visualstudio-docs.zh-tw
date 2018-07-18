---
title: 裝載 JavaScript 執行階段 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec744e-57cc-4ef5-8fe1-d2c27b946548
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bf213bf262ede7642e05c66e424b860238dc57f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569588"
---
# <a name="hosting-the-javascript-runtime"></a>裝載 JavaScript 執行階段
JavaScript Runtime (JsRT) API 藉由可同時在 Microsoft Edge 及 Internet Explorer 上使用的標準 Chakra JavaScript 引擎，為 Windows 作業系統上執行的桌面、Windows 市集及伺服器端應用程式提供加入指令碼的功能。 這些 API 可以在已安裝 Internet Explorer 11.0 的 Windows 10 及任何 Windows 作業系統版本上取得。 如需詳細資訊，請參閱 [Reference (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md). 如需在 Windows 市集應用程式中使用 JsRT 的相關資訊，請參閱 [JsRT and the Universal Windows Platform](#Windows)。  
  
> [!NOTE]
>  此文件適用於對 JavaScript 語言已掌握基礎知識的工作者。  
  
## <a name="concepts"></a>概念  
 要了解如何利用 JsRT API 操控 JavaScript 引擎，取決於兩個重要概念：執行階段和執行內容。  
  
 「 *執行階段* 」(Runtime) 代表一個完整的 JavaScript 執行環境。 每一個建立的執行階段都有各自獨立的記憶體回收堆積，而且根據預設，也有自己的 Just-In-Time (JIT) 編譯器執行緒和記憶體回收行程 (GC) 執行緒。 此 *執行內容* 代表 JavaScript 環境，其具有自己的 JavaScript 全域物件，與所有其他執行內容有所區分。 一個執行階段可以包含多個執行內容，而在這種情況下，所有執行內容會共用與該執行階段相關聯的 JIT 編譯器及 GC 執行緒，  
  
 執行階段代表單一執行緒。 在某一特定執行緒上一次只能有一個作用中的執行階段，而一個執行階段一次只能在一個執行緒上作用。 由於執行階段是以租用方式佔用執行緒，因此當某個執行階段目前未在執行緒上作用時 (也就是未執行任何 JavaScript 程式碼或回應任何主機呼叫)，就可以在任何尚未擁有作用中執行階段的執行緒上使用。  
  
 執行內容會繫結至特定執行階段，以及該執行階段內的執行程式碼。 與執行階段不同的是，一個執行緒上可以同時有多個作用中的執行內容。 因此，主機可以呼叫執行內容，該執行內容可以回呼主機，而且主機可以繼續呼叫其他執行內容。  
  
 ![多個執行內容](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting")  
  
 實際上，除非主機需要在個別的環境中執行程式碼，否則就可以使用單一執行內容。 同樣地，除非主機需要同時執行多段程式碼，否則只要單一執行階段就足夠。  
  
## <a name="memory-management"></a>記憶體管理  
 JavaScript 為記憶體回收語言，因此使用另一種語言處理 JsRT API 時務必記住幾項考量。  
  
 主要的考量在於 JavaScript 記憶體回收行程只能在兩個位置看到值的參考：一個位置是其執行階段的堆積，另一個是堆疊。 因此，當 JavaScript 值的參考儲存於另一個 JavaScript 值中或堆疊上的區域變數中時，記憶體回收行程將一律能看見該參考。 但是記憶體回收行程將無法看見儲存在其他位置 (例如，由主機或系統所管理的堆積) 的參考，進而可能導致提早回收主機仍在使用的值。  
  
> [!IMPORTANT]
>  某些語言編譯器 (例如 Visual Studio C++ 編譯器) 會盡可能將區域變數處理掉以進行最佳化。 但是如果要讓參考 JavaScript 值的區域變數保留這些值，則必須小心，確保這些變數位於堆疊上。  
  
 如果要將 JavaScript 值的參考儲存到記憶體回收行程無法看見的位置，則主機必須利用 JsRT API 手動加入和移除參考。  
  
## <a name="exception-handling"></a>例外狀況處理  
 當指令碼執行期間發生 JavaScript 例外狀況時，其中包含的執行階段就會進入例外狀況狀態。 處於例外狀況狀態時，所有程式碼都無法執行，而且任何 API 呼叫都會失敗並產生錯誤碼 `JsErrorInExceptionState` ，直到主機使用 `JsGetAndClearException` API 擷取並清除例外狀況，才可順利執行。 若主機自 JavaScript 回呼返回時並未清除執行階段的例外狀況狀態，則 JavaScript 例外狀況將在控制項傳回至 JavaScript 引擎時再次擲回。 這也可以讓主機回呼，以便藉由將執行階段設定為例外狀況狀態，然後自主機回呼返回的方式，「擲回」JavaScript 例外狀況。  
  
 主機不可將自己的內部例外狀況傳播至主機回呼，也就是說，所有回呼方法都必須先攔截所有主機例外狀況，才能將控制項回傳至執行階段。  
  
## <a name="runtime-resource-usage"></a>執行階段資源使用方式  
 JsRT API 提供了一些方法來監控及修改執行階段使用資源的方式。 這些方法通常細分為下列分類：  
  
-   **執行緒使用方式**： 根據預設，每個執行階段都會建立專用的 JIT 編譯器執行緒和專用的 GC 執行緒，為該執行階段提供服務。 如果建立的執行階段加上了 `JsRuntimeAttributeDisableBackgroundWork` 旗標，則 JIT 和 GC 的工作會在該執行階段的執行緒本身上執行，而不是另外在個別的不同背景執行緒上執行。 主機也可以對 `JsCreateRuntime` 呼叫提供執行緒服務回呼，讓主機得以透過適當的方式排程 JIT 和 GC 的工作。  
  
-   **記憶體使用量**。 有幾種方式可監控及修改執行階段的記憶體使用方式。 如果執行階段將長時間執行，主機可以在建立執行階段時指定 `JsRuntimeAttributeEnableIdleProcessing` 旗標，然後在主機處於閒置狀態時呼叫 `JsIdle` 。 這樣可讓引擎將一些記憶體清除和簿記工作延後到閒置時進行。  
  
     主機可以透過呼叫 `JsSetRuntimeBeforeCollectCallback`監視記憶體回收， 也可以藉由呼叫 `JsSetRuntimeMemoryAllocationCallback`監視堆積的配置情形。 請注意，此 API 不會在每次 JavaScript 配置時回呼，只有在執行階段的堆積需要更多空間進行配置時才回呼。 記憶體配置回呼可以拒絕要求，這樣將會觸發記憶體回收，而如果沒有可用的記憶體，則會在執行階段觸發記憶體不足的錯誤。  
  
     主機也可以呼叫 `JsSetRuntimeMemoryLimit` 來設定執行階段可以使用的記憶體限制。 當執行階段達到記憶體限制時，將會觸發記憶體回收，而如果沒有可用的記憶體，則執行階段會擲回記憶體不足的錯誤。  
  
-   **指令碼中斷和評估**： 主機可以呼叫 `JsDisableRuntimeExecution` 來結束執行階段內的執行動作。 此呼叫可以隨時從任何執行緒進行。 由於指令碼結束取決於是否到達程式碼中插入的保護點，因此指令碼不一定會在確切的時間點結束，而是在經過短暫片刻後結束。 根據預設，結束保護點會以穩當的方式放入產生的程式碼中，且不一定會涵蓋所有情況，例如無限迴圈。 建立具有 `JsRuntimeAttributeAllowScriptInterrupt` 旗標的執行階段會造成執行階段插入額外的無限迴圈檢查，通常這樣會造成輕微的效能負荷。  
  
     如果主機希望禁止 JIT 編譯器產生機器碼，可以指定 `JsRuntimeAttributeDisableNativeCodeGeneration` 旗標。 主機也可以藉由指定 `JsRuntimeAttributeDisableEval` 旗標禁止指令碼動態自行執行。  
  
## <a name="debugging-and-profiling"></a>偵錯和分析  
 JsRT API 透過 Active Scripting 技術支援偵錯和程式碼剖析。  
  
 從 Windows 10 開始，Chakra JavaScript 引擎即支援舊版的引擎和 Edge 引擎，因此在 JsRT 中您可以其中一項為目標 (請參閱[以 Edge 和舊版引擎為目標](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)以取得詳細資料)。 在舊版和 Edge 引擎中，Visual Studio 的偵錯指令碼運作方式不同。 若使用舊版引擎，主機需要提供 [IDebugApplication 介面](../winscript/reference/idebugapplication-interface.md)指標，其可從 [IProcessDebugManager 介面](../winscript/reference/iprocessdebugmanager-interface.md)執行個體取得。 若使用 Edge 引擎， `IDebugApplication` 已被取代；Chakra 引擎可透過 Visual Studio 偵錯工具執行原生和指令碼偵錯功能，而不需要使用者實作 `IDebugApplication` 。  
  
 為了能夠在執行內容中對指令碼進行偵錯，Chakra 引擎必須改採效率較差的程式碼執行方法。 如此一來，可偵錯程式碼的執行速度通常會比不可偵錯的程式碼來得慢。 因此，若使用舊版引擎，主機可以選擇在執行內容 `IDebugApplication` 開頭提供 `JsCreateContext`指標的方式開始進行偵錯，或是等到需要偵錯時再呼叫 `JsStartDebugging`。 若使用 Edge 引擎， `JsCreateContext` 已不再使用 `IDebugApplication` 參數，因此僅有在呼叫 `JsStartDebugging` 後才能偵錯指令碼。 使用 Visual Studio 進行偵錯時，必須啟用 "Script" 偵錯工具選項。  
  
 執行內容中的 JavaScript 程式碼可以透過兩種方式進行剖析。 一種方式是在 Windows 8.1 (含) 以上版本中使用命令列 Visual Studio 分析工具 (vsperf.exe) 搭配 /js 參數，以產生針對應用程式中所執行之 JavaScript 程式碼的報告。 另一種方式是，主機可以直接呼叫 `JsStartProfiling` 和 `JsStopProfiling` ，並提供回呼來進行程式碼剖析。 主機也可以藉由呼叫 `JsEnumerateHeap`檢查記憶體回收堆積的狀態。 舊版和 Edge 引擎的 JsRT 程式碼剖析運作方式相同。 不過，JsRT 程式碼剖析 API (`JsStartProfiling`、 `JsStopProfiling`、 `JsEnumerateHeap`以及 `JsIsEnumeratingHeap`) 不適用於通用的 Windows 應用程式。  
  
<a name="Windows"></a>   
## <a name="jsrt-and-the-universal-windows-platform"></a>JsRT and the Universal Windows Platform  
 您可使用 JsRT API 將指令碼功能加入通用的 Windows 應用程式。 使用 JsRT API 的通用 Windows 應用程式必須以 Edge JSRT API 為目標，也就是以 Edge Chakra 引擎為目標。 如需詳細資訊，請參閱[以 Edge 和舊版引擎為目標](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)。 除了程式碼剖析和堆積列舉支援 (但不支援`JsStartProfiling`、 `JsStopProfiling`、 `JsEnumerateHeap`和 `JsIsEnumeratingHeap` ) 以外，完整的 JsRT API 還可用於通用 Windows 應用程式。  
  
 透過 Edge JsRT API `JsProjectWinRTNamespace` 公開 API 命名空間之後，JsRT 也可讓指令碼以原生方式存取任何[通用 Windows 平台 (UWP) API](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx)。 雖然通用 Windows 應用程式只需對應出必要的命名空間，而不需其他設定，但在傳統 (Win32) Windows 應用程式中，COM 初始化委派提取機制需透過 `JsSetProjectionEnqueueCallback` 啟用事件和非同步 API 才能啟用。 下列的 Win32 範例會利用非同步 UWP API 來建立 http 用戶端並從 Uri 取得內容：  
  
```cpp  
typedef struct _jsCall {  
    JsProjectionCallback jsCallback;  
    JsProjectionCallbackContext jsContext;  
    HANDLE event;  
} jsCall;  
  
// Set up delegated pumping mechanism; not necessary in UWP applications.  
jsCall outstandingCall = {};  
CoInitializeEx(nullptr, COINIT_MULTITHREADED);  
JsSetProjectionEnqueueCallback([](JsProjectionCallback jsCallback,   
JsProjectionCallbackContext jsContext, void *callbackState) {  
    jsCall* call = (jsCall*)callbackState;  
    call->jsCallback = jsCallback;  
    call->jsContext = jsContext;  
    SetEvent(call->event);  
    },  
&outstandingCall);  
HANDLE event = CreateEventEx(NULL, NULL, CREATE_EVENT_MANUAL_RESET, EVENT_ALL_ACCESS);  
outstandingCall.event = event;  
  
// Project necessary namespaces.  
JsProjectWinRTNamespace(L"Windows.Foundation");  
JsProjectWinRTNamespace(L"Windows.Web");  
  
// Get content from an Uri.  
JsRunScript(L"var uri = new Windows.Foundation.Uri(\"http://somedatasource.com\"); " \  
    L"var httpClient = new Windows.Web.Http.HttpClient();" \  
    L"httpClient.getStringAsync(uri).done(function (content) { " \  
    L"    // do something with the string content " \    
    L"}, onError); " \  
    L"function onError(reason) { " \  
    L"    // error handling " \        
    L"}",   
    currentSourceContext, L"", &result);  
  
// Wait for async call to come in and then execute; not necessary in UWP applications.  
WaitForSingleObjectEx(outstandingCall.event, 10000, FALSE) == WAIT_OBJECT_0;  
outstandingCall.jsCallback(outstandingCall.jsContext);  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 執行階段範例應用程式](http://go.microsoft.com/fwlink/p/?LinkID=306674&clcid=0x409)   
 [參考 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)   
 [JavaScript 執行階段裝載](../chakra-hosting/javascript-runtime-hosting.md)