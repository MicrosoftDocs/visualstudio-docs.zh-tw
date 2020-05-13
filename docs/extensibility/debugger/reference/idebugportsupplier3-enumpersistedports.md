---
title: IDebugPort供應商3::枚舉保留埠 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92b31a6b6898b0031e4a01d5a6433d0ce77e64f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724448"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
此方法檢索允許枚舉持久化埠清單的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>參數
`PortNames`\
[在]包含要在持久埠之間查找和返回的埠名稱清單[BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)結構。 將僅返回具有這些名稱的持久化埠。

`ppEnum`\
[出]實現[IEnum DebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)介面的物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 實例化埠供應商時載入持久埠,並在埠供應商銷毀時保存。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
