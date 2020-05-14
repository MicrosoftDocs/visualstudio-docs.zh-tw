---
title: IDebug 待定斷點2::setPassCount |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 732eadc955b9a6c9bdded3d52f038ff58ed9c217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725674"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
設置或更改與掛起斷點關聯的傳遞計數。

## <a name="syntax"></a>語法

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>參數
`bpPassCount`\
[在]包含通過計數的[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)結構。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_BP_DELETED`斷點已被刪除,則返回。

## <a name="remarks"></a>備註
 以前與掛起的斷點關聯的任何通過計數都將丟失。 調用來自此掛起斷點的所有斷點,以將其通過計數設置為`bpPassCount`參數。

## <a name="see-also"></a>另請參閱
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
