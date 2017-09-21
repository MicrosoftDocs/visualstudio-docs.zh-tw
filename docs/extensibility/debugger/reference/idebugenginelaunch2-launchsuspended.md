---
title: "IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會將處理程序啟動的偵錯引擎 \(DE\)。  
  
## 語法  
  
```cpp#  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```c#  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### 參數  
 `pszMachine`  
 \[in\]用來啟動處理序的電腦名稱。  若要指定本機電腦使用 null 值。  
  
 `pPort`  
 \[in\][IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)表示該程式將執行中的連接埠的介面。  
  
 `pszExe`  
 \[in\]若要啟動的可執行檔名稱。  
  
 `pszArgs`  
 \[in\]要傳遞至可執行檔的引數。  如果沒有引數時，就可能為 null 值。  
  
 `pszDir`  
 \[in\]可執行檔所使用之工作目錄的名稱。  如果沒有工作目錄不需要時，就可能為 null 值。  
  
 `bstrEnv`  
 \[in\]環境區塊的 NULL 終端字串，後面接著詳細的 NULL 結束字元。  
  
 `pszOptions`  
 \[in\]可執行檔的選項。  
  
 `dwLaunchFlags`  
 \[in\]指定[LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)工作階段。  
  
 `hStdInput`  
 \[in\]替代的輸入資料流的控制代碼。  如果不是必要的重新導向時，就可能是 0。  
  
 `hStdOutput`  
 \[in\]其他輸出資料流的控制代碼。  如果不是必要的重新導向時，就可能是 0。  
  
 `hStdError`  
 \[in\]其他的錯誤輸出資料流的控制代碼。  如果不是必要的重新導向時，就可能是 0。  
  
 `pCallback`  
 \[in\][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)接收偵錯工具事件的物件。  
  
 `ppDebugProcess`  
 \[\] out傳回所產生的[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，代表在啟動程序。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 一般情況下， [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]啟動程式，使用[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)方法，然後再附加偵錯工具，來暫停程式。  然而，有一些情況下，在此情況下啟動的程式 \(例如，如果偵錯引擎會解譯器的一部分，而且偵錯的程式是解譯的語言\)，可能需要偵錯引擎[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]會使用`IDebugEngineLaunch2::LaunchSuspended`方法。  
  
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)的處理序已成功啟動在暫停狀態後，啟動程序呼叫方法。  
  
## 請參閱  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)