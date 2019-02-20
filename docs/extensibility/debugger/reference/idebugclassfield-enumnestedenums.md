---
title: IDebugClassField::EnumNestedEnums |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec2bd27ffdecb41aa60b38dd7b8202c7c6449637
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412860"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
建立這個類別的巢狀的列舉值的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>參數
`ppEnum`  
[out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示巢狀的列舉型別的清單。 如果不有任何巢狀列舉型別，則傳回 null 值。

## <a name="return-value"></a>傳回值
如果成功，會傳回 S_OK，或如果沒有任何巢狀的列舉值，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
列舉型別的每個項目是[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)物件，描述巢狀的列舉型別。

在類別內宣告的列舉型別會被視為巢狀的列舉型別。 例如，假設︰

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

`EnumNestedEnums`方法會傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，其中包含一個[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)物件，表示`NestedEnum`列舉型別。

## <a name="see-also"></a>另請參閱
[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)  
[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)  
[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
