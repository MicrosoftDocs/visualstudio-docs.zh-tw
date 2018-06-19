---
title: IDebugEngineLaunch2::LaunchSuspended |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a05e8f034ec30f0f387675759cb7601f7b3fc3e7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114621"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
這個方法會藉由偵錯引擎 (DE) 啟動處理程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>參數  
 `pszMachine`  
 [in]用來啟動處理序中的機器名稱。 若要指定本機電腦中使用 null 值。  
  
 `pPort`  
 [in][IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面代表程式將執行中的連接埠。  
  
 `pszExe`  
 [in]若要啟動之可執行檔名稱。  
  
 `pszArgs`  
 [in]要傳遞給可執行檔引數。 可能是 null 值，如果不有任何引數。  
  
 `pszDir`  
 [in]可執行檔所使用的工作目錄名稱。 可能是 null 值，如果沒有工作目錄是必要。  
  
 `bstrEnv`  
 [in]以 NULL 結束的字串，後面接著其他的 NULL 結束字元的環境區塊。  
  
 `pszOptions`  
 [in]可執行檔選項。  
  
 `dwLaunchFlags`  
 [in]指定[LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)工作階段。  
  
 `hStdInput`  
 [in]替代的輸入資料流的控制代碼。 如果不需要重新導向，則可能是 0。  
  
 `hStdOutput`  
 [in]替代輸出資料流的控制代碼。 如果不需要重新導向，則可能是 0。  
  
 `hStdError`  
 [in]替代錯誤輸出資料流的控制代碼。 如果不需要重新導向，則可能是 0。  
  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)接收偵錯工具事件的物件。  
  
 `ppDebugProcess`  
 [out]傳回所產生的[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，代表啟動的程序。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 一般來說，[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]啟動程式，使用[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)方法，然後將偵錯工具附加至暫止的程式。 不過，有一些情況下，偵錯引擎可能需要在此情況下啟動的程式 （例如，如果偵錯引擎是解譯器的一部分，而且正在偵錯的程式是解譯的語言），[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]使用`IDebugEngineLaunch2::LaunchSuspended`方法.  
  
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)方法來啟動處理程序已成功啟動在暫停狀態之後呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)