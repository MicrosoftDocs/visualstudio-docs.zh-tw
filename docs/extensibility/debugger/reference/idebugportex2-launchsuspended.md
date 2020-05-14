---
title: IDebugPortEx2::啟動暫停 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725106"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
啟動可執行檔。

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

## <a name="parameters"></a>參數
`pszExe`\
[在]要啟動的可執行檔的名稱。 這可以是完整路徑,也可以與`pszDir`參數中指定的工作目錄相關。

`pszArgs`\
[在]要傳遞給可執行檔的參數。 如果沒有參數,則可能是 null 值。

`pszDir`\
[在]可執行檔使用的工作目錄的名稱。 如果不需要工作目錄,則可能是空值。

`bstrEnv`\
[在]null 終止字串的環境塊,後跟一個額外的 NULL 終止符。

`hStdInput`\
[在]處理備用輸入流。 如果不需要重定向,則可能是 0。

`hStdOutput`\
[在]處理備用輸出流。 如果不需要重定向,則可能是 0。

`hStdError`\
[在]處理備用錯誤輸出流。 如果不需要重定向,則可能是 0。

`ppPortProcess`\
[出]返回表示啟動進程的[IDebug PendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法應啟動進程,以便它掛起並且不運行任何代碼。 調用[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)方法以恢復該過程。

 也可以從調試引擎啟動程式。 有關詳細資訊,請參閱[啟動程式](../../../extensibility/debugger/launching-a-program.md)。

## <a name="see-also"></a>另請參閱
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [啟動程式](../../../extensibility/debugger/launching-a-program.md)
