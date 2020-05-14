---
title: IDebugEngine啟動2::啟動暫停 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730551"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
此方法通過調試引擎 (DE) 啟動進程。

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
[在]要在其中啟動進程的機器的名稱。 使用 null 值指定本地電腦。

`pPort`\
[在][IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面表示程式將在其中運行的埠。

`pszExe`\
[在]要啟動的可執行檔的名稱。

`pszArgs`\
[在]要傳遞給可執行檔的參數。 如果沒有參數,則可能是 null 值。

`pszDir`\
[在]可執行檔使用的工作目錄的名稱。 如果不需要工作目錄,則可能是空值。

`bstrEnv`\
[在]NULL 終止字串的環境塊,後跟一個額外的 NULL 終止符。

`pszOptions`\
[在]可執行檔的選項。

`dwLaunchFlags`\
[在]指定會話[的LAUNCH_FLAGS。](../../../extensibility/debugger/reference/launch-flags.md)

`hStdInput`\
[在]處理備用輸入流。 如果不需要重定向,則可能是 0。

`hStdOutput`\
[在]處理備用輸出流。 如果不需要重定向,則可能是 0。

`hStdError`\
[在]處理備用錯誤輸出流。 如果不需要重定向,則可能是 0。

`pCallback`\
[在]接收調試器事件的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件。

`ppDebugProcess`\
[出]返回表示啟動過程的結果[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 通常,[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]使用[Launch 暫停](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)方法啟動程式,然後將除錯器附加到掛起的程式。 但是,在某些情況下,調試引擎可能需要啟動程式(例如,如果調試引擎是解釋器的一部分,並且正在調試的程式是解釋語言),在這種情況下[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)],使用 該`IDebugEngineLaunch2::LaunchSuspended`方法。

 在進程以掛起狀態成功啟動后,將調用[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)方法以啟動進程。

## <a name="see-also"></a>另請參閱
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
