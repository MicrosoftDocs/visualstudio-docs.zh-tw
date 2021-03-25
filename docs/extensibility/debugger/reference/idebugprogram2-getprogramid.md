---
description: 取得此程式的 GUID。
title: IDebugProgram2：： GetProgramId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad0b5c8af1723414e6805e362312f167f995fbe4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084502"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
取得此程式的 GUID。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>參數
`pguidProgramId`\
擴展傳回 `GUID` 此程式的。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 Debug engine (DE) 必須傳回原本傳遞給 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 或 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法的程式識別碼。 這可讓您跨偵錯工具元件識別程式。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
