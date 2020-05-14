---
title: IEnumDebug綁定斷點2::克隆 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Clone
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Clone
ms.assetid: c6ce01a2-7da3-46ec-9837-855042fa7244
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b10289a713642960b03c1a51775148357b8a3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717570"
---
# <a name="ienumdebugboundbreakpoints2clone"></a>IEnumDebugBoundBreakpoints2::Clone
將當前枚舉的副本作為單獨的物件返回。

## <a name="syntax"></a>語法

```cpp
HRESULT Clone(
   IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]將此枚舉的副本作為單獨的物件返回。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 枚舉的副本在調用此方法時與原始副本具有相同的狀態。 但是,副本和原始副本的狀態是分開的,可以單獨更改。

## <a name="see-also"></a>另請參閱
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
