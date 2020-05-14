---
title: IDebugCoreServer2::枚舉 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::EnumPorts
helpviewer_keywords:
- IDebugCoreServer2::EnumPorts
ms.assetid: 3d98dfd0-614f-4d68-90c6-8a9b9cab66f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e72c87bfe7649b483e744cbccffa93d7ad721a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733194"
---
# <a name="idebugcoreserver2enumports"></a>IDebugCoreServer2::EnumPorts
檢索所有可用埠的清單。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumPorts( 
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPorts( 
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]返回包含來自所有埠供應商的所有埠的清單的[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
