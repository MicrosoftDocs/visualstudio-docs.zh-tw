---
description: 取得 debug engine (DE) 的 GUID。
title: IDebugEngine2：： GetEngineID |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf785c906303bab677adadfd081ae6af276a754c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153972"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
取得 debug engine (DE) 的 GUID。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

## <a name="parameters"></a>參數
`pguidEngine`\
擴展傳回 DE 的 GUID。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
一般 Guid 的一些範例包括 `guidScriptEng` 、 `guidNativeEng` 或 `guidSQLEng` 。 新的偵錯工具引擎會建立自己的 GUID 以供識別。

## <a name="example"></a>範例
下列範例示範如何針對實 IDebugEngine2 介面的簡單物件，執行這個方法 `CEngine` 。 [](../../../extensibility/debugger/reference/idebugengine2.md)

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
