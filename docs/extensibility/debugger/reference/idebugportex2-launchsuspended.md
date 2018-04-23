---
title: IDebugPortEx2::LaunchSuspended |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f22afc50a1a2874d4853acbf9ff72cae622e790
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
會啟動可執行檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>參數  
 `pszExe`  
 [in]若要啟動之可執行檔名稱。 這可以是完整路徑或指定的工作目錄的相對`pszDir`參數。  
  
 `pszArgs`  
 [in]要傳遞給可執行檔引數。 可能是 null 值，如果不有任何引數。  
  
 `pszDir`  
 [in]可執行檔所使用的工作目錄名稱。 可能是 null 值，如果沒有工作目錄是必要。  
  
 `bstrEnv`  
 [in]以 null 結束的字串，後面接著其他的 NULL 結束字元的環境區塊。  
  
 `hStdInput`  
 [in]替代的輸入資料流的控制代碼。 如果不需要重新導向，則可能是 0。  
  
 `hStdOutput`  
 [in]替代輸出資料流的控制代碼。 如果不需要重新導向，則可能是 0。  
  
 `hStdError`  
 [in]替代錯誤輸出資料流的控制代碼。 如果不需要重新導向，則可能是 0。  
  
 `ppPortProcess`  
 [out]傳回[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)物件，代表啟動的程序。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法應啟動的程序，所以它已暫止，但未執行任何程式碼。 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)呼叫方法來繼續執行程序。  
  
 也可以從偵錯引擎啟動程式。 如需詳細資訊，請參閱[啟動程式](../../../extensibility/debugger/launching-a-program.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [啟動程式](../../../extensibility/debugger/launching-a-program.md)