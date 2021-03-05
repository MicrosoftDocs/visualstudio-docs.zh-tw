---
description: 判斷是否可以終止進程。
title: IDebugEngineLaunch2：： CanTerminateProcess |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 687b2816c6fd312efef29daa44e0644fc5c5c8c6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153621"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
判斷是否可以終止進程。

## <a name="syntax"></a>語法

```cpp
HRESULT CanTerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int CanTerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>參數
`pProcess`\
在 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 物件，表示要結束的進程。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 `S_FALSE`如果引擎無法終止進程（例如，因為拒絕存取），則會傳回。

## <a name="remarks"></a>備註
 如果這個方法傳回 `S_OK` ，則可以呼叫 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) 方法，以實際終止進程。

## <a name="see-also"></a>另請參閱
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)
