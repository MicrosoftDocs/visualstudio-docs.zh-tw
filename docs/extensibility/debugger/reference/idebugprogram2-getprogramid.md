---
title: IDebugProgram2::獲取程式Id |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bb172f48b63ef2ec182f1a83d599a91eff1e2ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722768"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
獲取此程式的 GUID。

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
[出]傳回`GUID`此 程式的 。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 除錯引擎 (DE) 必須返回最初傳遞給[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)或[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法的程式識別符。 這允許跨調試器元件標識程式。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
