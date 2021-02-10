---
title: IDebugErrorBreakpoint2：： GetPendingBreakpoint |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugErrorBreakpoint2::GetPendingBreakpoint
ms.assetid: 59d0defc-99fd-445c-bdac-8224d5dea3f9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50bed9b3bbfcfce660455a3e62676593d6429b57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946861"
---
# <a name="idebugerrorbreakpoint2getpendingbreakpoint"></a>IDebugErrorBreakpoint2::GetPendingBreakpoint
取得造成錯誤的暫止中斷點。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPendingBreakpoint ( 
   IDebugPendingBreakpoint2** ppPendingBreakpoint
);
```

```csharp
int GetPendingBreakpoint ( 
   out IDebugPendingBreakpoint2 ppPendingBreakpoint
);
```

## <a name="parameters"></a>參數
`ppPendingBreakpoint`\
擴展傳回 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 物件，這個物件表示無法系結的暫止中斷點。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
