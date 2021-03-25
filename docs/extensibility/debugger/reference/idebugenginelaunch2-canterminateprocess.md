---
description: 判斷是否可以終止進程。
title: IDebugEngineLaunch2：： CanTerminateProcess |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20df2c6d44e9bb0afd6610d6ded01ed637035b4b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077443"
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
