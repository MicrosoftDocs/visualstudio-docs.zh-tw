---
title: IDebugPortEx2：： LaunchSuspended |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3cfaf6dd332f17bd934a55f700e4d28096fba8b8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844771"
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
在要啟動的可執行檔名稱。 這可以是完整路徑或相對於參數中所指定的工作目錄 `pszDir` 。

`pszArgs`\
在要傳遞給可執行檔的引數。 如果沒有引數，則可以是 null 值。

`pszDir`\
在可執行檔所使用之工作目錄的名稱。 如果不需要工作目錄，則可以是 null 值。

`bstrEnv`\
在以 null 結束之字串的環境區塊，後面接著額外的 Null 結束字元。

`hStdInput`\
在替代輸入資料流程的控制碼。 如果不需要重新導向，則可以是0。

`hStdOutput`\
在替代輸出資料流程的控制碼。 如果不需要重新導向，則可以是0。

`hStdError`\
在替代錯誤輸出資料流程的控制碼。 如果不需要重新導向，則可以是0。

`ppPortProcess`\
擴展傳回代表已啟動進程的 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法應該會啟動進程，使其暫停且不執行任何程式碼。 呼叫 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) 方法以繼續處理常式。

 您也可以從 debug engine 啟動程式。 如需詳細資訊，請參閱 [啟動程式](../../../extensibility/debugger/launching-a-program.md)。

## <a name="see-also"></a>另請參閱
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [啟動程式](../../../extensibility/debugger/launching-a-program.md)
