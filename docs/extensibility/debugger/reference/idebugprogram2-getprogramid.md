---
title: IDebugProgram2::GetProgramId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aba5ac3e17cb86219c065b5ed2372e127ad03dd2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320774"
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
[out]傳回`GUID`此計劃。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 偵錯引擎 (DE) 必須傳回原本傳遞至程式識別碼[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)或是[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。 這可讓程式識別在偵錯工具元件。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)