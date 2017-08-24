---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 2020dbb883f7de5efbbe7642bc0d07720a3dab3e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Launches an executable file.  
  
## <a name="syntax"></a>Syntax  
  
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
  
```cs  
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
  
#### <a name="parameters"></a>Parameters  
 `pszExe`  
 [in] The name of the executable to be launched. This can be a full path or relative to the working directory specified in the `pszDir` parameter.  
  
 `pszArgs`  
 [in] The arguments to pass to the executable. May be a null value if there are no arguments.  
  
 `pszDir`  
 [in] The name of the working directory used by the executable. May be a null value if no working directory is required.  
  
 `bstrEnv`  
 [in] Environment block of null-terminated strings, followed by an additional NULL terminator.  
  
 `hStdInput`  
 [in] Handle to an alternate input stream. May be 0 if redirection is not required.  
  
 `hStdOutput`  
 [in] Handle to an alternate output stream. May be 0 if redirection is not required.  
  
 `hStdError`  
 [in] Handle to an alternate error output stream. May be 0 if redirection is not required.  
  
 `ppPortProcess`  
 [out] Returns an [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) object that represents the launched process.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 This method should launch the process so that it is suspended and not running any code. The [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) method is called to resume the process.  
  
 A program can also be launched from a debug engine. For details, see [Launching a Program](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>See Also  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Launching a Program](../../../extensibility/debugger/launching-a-program.md)
