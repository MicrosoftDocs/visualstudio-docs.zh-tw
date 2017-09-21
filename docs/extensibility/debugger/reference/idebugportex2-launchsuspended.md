---
title: "IDebugPortEx2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

啟動可執行檔。  
  
## 語法  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```c#  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### 參數  
 `pszExe`  
 \[in\]若要啟動的可執行檔名稱。  這可以是完整的路徑或相對於指定的工作目錄`pszDir`參數。  
  
 `pszArgs`  
 \[in\]要傳遞至可執行檔的引數。  如果沒有引數時，就可能為 null 值。  
  
 `pszDir`  
 \[in\]可執行檔所使用之工作目錄的名稱。  如果沒有工作目錄不需要時，就可能為 null 值。  
  
 `bstrEnv`  
 \[in\]環境區塊的 null 終端字串，後面接著詳細的 NULL 結束字元。  
  
 `hStdInput`  
 \[in\]替代的輸入資料流的控制代碼。  如果不是必要的重新導向時，就可能是 0。  
  
 `hStdOutput`  
 \[in\]其他輸出資料流的控制代碼。  如果不是必要的重新導向時，就可能是 0。  
  
 `hStdError`  
 \[in\]其他的錯誤輸出資料流的控制代碼。  如果不是必要的重新導向時，就可能是 0。  
  
 `ppPortProcess`  
 \[\] out傳回[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)物件，代表在啟動程序。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法應該啟動程序，以便確定它已暫停，但並未執行任何程式碼。  [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)著繼續執行處理程序呼叫方法。  
  
 也可以從 \[偵錯引擎啟動程式。  如需詳細資訊，請參閱 [啟動程式](../../../extensibility/debugger/launching-a-program.md)。  
  
## 請參閱  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [啟動程式](../../../extensibility/debugger/launching-a-program.md)