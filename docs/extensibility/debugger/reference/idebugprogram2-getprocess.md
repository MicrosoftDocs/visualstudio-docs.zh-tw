---
description: 取得此程式執行所在的進程。
title: IDebugProgram2：： GetProcess |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d87d863b954a9865ff3960f2f2cdd45ac40ce58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065394"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
取得此程式執行所在的進程。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>參數
`ppProcess`\
擴展傳回表示進程的 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 除非 debug engine (DE) 實 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) 介面，否則這個方法的執行應該一律會傳回， `E_NOTIMPL` 因為 de 無法判斷正在執行的進程，因此無法滿足此方法的執行。

 實作為 `IDebugEngineLaunch2` 介面表示，de 必須知道如何建立進程，因此， [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面的 de 實，可以知道它正在執行的程式。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
