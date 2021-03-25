---
description: 建立容器欄位的列舉值。
title: IDebugContainerField：： EnumFields |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63ce34fc9eddec84326982cf7d30fda919817040
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077924"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
建立容器欄位的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>參數
`dwKindFilter`\
在 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 常數的組合，可選取要列舉的欄位。 欄位種類可以描述儲存體類型，例如類別或基本型別，或特定的資訊，例如 local、parameter 或 "this" 指標。

`dwModifiersFilter`\
在 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) 常數的組合，可選取要列舉的欄位。 欄位修飾詞可以是存取權限，例如公用或私用或儲存體資訊，例如虛擬、靜態或最終。

`pszNameFilter`\
在要列舉之欄位的名稱。 如果要傳回所有欄位，這可以是 null 值。

`nameMatch`\
在 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) 列舉中的值，可控制搜尋是否區分大小寫。

`ppEnum`\
擴展傳回代表欄位清單的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件。 如果沒有任何欄位，則傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK 或 S_FALSE （如果沒有任何欄位）。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 `dwKindFilter`例如， `dwModifiersFilter` `pszNameFilter` 可以合併、和參數，以選取所有名為 "MyMethod" 的公用虛擬方法。

## <a name="see-also"></a>另請參閱
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
