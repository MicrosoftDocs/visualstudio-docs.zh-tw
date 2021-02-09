---
title: IDebugEngineLaunch2：： LaunchSuspended |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1afa09abd0e997c47b33953e5321d4c5d1845a25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892823"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
這個方法會透過 debug engine (DE) 來啟動處理常式。

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

## <a name="parameters"></a>參數
`pszMachine`\
在要在其中啟動處理常式的電腦名稱稱。 使用 null 值來指定本機電腦。

`pPort`\
在代表程式將在其中執行之埠的 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 介面。

`pszExe`\
在要啟動的可執行檔名稱。

`pszArgs`\
在要傳遞給可執行檔的引數。 如果沒有引數，則可以是 null 值。

`pszDir`\
在可執行檔所使用之工作目錄的名稱。 如果不需要工作目錄，則可以是 null 值。

`bstrEnv`\
在以 Null 結束之字串的環境區塊，後面接著額外的 Null 結束字元。

`pszOptions`\
在可執行檔的選項。

`dwLaunchFlags`\
在指定會話的 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) 。

`hStdInput`\
在替代輸入資料流程的控制碼。 如果不需要重新導向，則可以是0。

`hStdOutput`\
在替代輸出資料流程的控制碼。 如果不需要重新導向，則可以是0。

`hStdError`\
在替代錯誤輸出資料流程的控制碼。 如果不需要重新導向，則可以是0。

`pCallback`\
在接收偵錯工具事件的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 物件。

`ppDebugProcess`\
擴展傳回產生的 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 物件，代表已啟動的進程。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 一般來說，會 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 使用 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) 方法啟動程式，然後將偵錯工具附加至已暫止的程式。 不過，在某些情況下，debug engine 可能需要啟動程式 (例如，如果偵錯工具是解譯器的一部分，而正在進行調試的程式是) 的解讀語言，在這種情況下會 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 使用 `IDebugEngineLaunch2::LaunchSuspended` 方法。

 在以暫停狀態成功啟動程式之後，會呼叫 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) 方法來啟動處理常式。

## <a name="see-also"></a>另請參閱
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
