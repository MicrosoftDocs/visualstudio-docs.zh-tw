---
description: 這個方法會抓取可列舉保存埠清單的物件。
title: IDebugPortSupplier3：： EnumPersistedPorts |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 582849f0dd859d5155b4d3ee5653cefff6396780
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150415"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
這個方法會抓取可列舉保存埠清單的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>參數
`PortNames`\
在 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) 結構，其中包含要在保存的埠之間尋找並傳回的埠名稱清單。 只會傳回具有這些名稱的持續性埠。

`ppEnum`\
擴展實 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) 介面的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 當埠供應商具現化時，會載入保存的埠，並在埠供應商終結時儲存。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
