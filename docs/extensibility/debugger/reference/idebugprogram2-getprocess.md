---
title: IDebugProgram2::獲取過程 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722789"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
獲取此程式正在運行的進程。

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
[出]返回表示進程的[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 除非調試引擎 (DE) 實現[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)介面,否則 DE 此`E_NOTIMPL`方法的實現應始終返回 ,因為 DE 無法確定它在哪個進程中運行,因此無法滿足此方法的實現。

 實現`IDebugEngineLaunch2`介面意味著 DE 必須知道如何創建進程;因此,DE [IDebug Program2](../../../extensibility/debugger/reference/idebugprogram2.md)介面的實現能夠知道它正在運行的進程。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
