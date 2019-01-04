---
title: IDebugPortEx2::LaunchSuspended |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 5166e63244d8f437460136b4c116ac148f029919
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876951"
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
 [in]若要啟動的可執行檔名稱。 這可以是完整路徑或相對於在指定的工作目錄`pszDir`參數。  
  
 `pszArgs`  
 [in]要傳遞至可執行檔的引數。 如果不有任何引數，則可能是 null 值。  
  
 `pszDir`  
 [in]可執行檔所使用的工作目錄名稱。 可能是 null 值，如果所沒有的工作目錄。  
  
 `bstrEnv`  
 [in]Null 終止的字串，後面接著其他的 NULL 結束字元的環境區塊。  
  
 `hStdInput`  
 [in]替代的輸入資料流的控制代碼。 如果不需要重新導向，則可能是 0。  
  
 `hStdOutput`  
 [in]替代的輸出資料流的控制代碼。 如果不需要重新導向，則可能是 0。  
  
 `hStdError`  
 [in]替代錯誤輸出資料流的控制代碼。 如果不需要重新導向，則可能是 0。  
  
 `ppPortProcess`  
 [out]傳回[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)物件，表示啟動的程序。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法應該啟動的程序，因此它會暫停，而未執行任何程式碼。 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)呼叫方法來繼續此程序。  
  
 也可以從 偵錯引擎啟動程式。 如需詳細資訊，請參閱 <<c0> [ 啟動程式](../../../extensibility/debugger/launching-a-program.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [啟動程式](../../../extensibility/debugger/launching-a-program.md)