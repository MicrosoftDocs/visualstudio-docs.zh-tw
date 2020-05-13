---
title: IDebug位址2::獲取進程ID |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94873e9a9c05a0c5e9253ce53240ab6b4ca39064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736585"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
檢索擁有此[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)介面表示的物件的進程的 ID。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>參數
`pProcID`\
[出]進程識別碼。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
