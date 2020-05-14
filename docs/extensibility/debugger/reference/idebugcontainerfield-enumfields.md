---
title: IDebug容器欄位::枚舉場 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733232"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
為容器的欄位創建枚舉器。

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
[在]選擇要枚舉的欄位[的FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)常量的組合。 欄位型態可以描述儲存類型,如類或基元,或特定資訊,如本地、參數或"此"指標。

`dwModifiersFilter`\
[在]選擇要枚舉的欄位的[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)常量的組合。 欄位修改器可以是存取許可權(如公共或私有)或儲存資訊(如虛擬、靜態或最終)。

`pszNameFilter`\
[在]要枚舉的欄位的名稱。 如果要返回所有欄位,這可以為空值。

`nameMatch`\
[在][NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)枚舉中的值,用於控制搜索是否區分大小寫。

`ppEnum`\
[出]返回表示欄位清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件。 如果沒有欄位,則返回空值。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK或S_FALSE如果沒有欄位。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 可以`dwKindFilter`組合`dwModifiersFilter`和`pszNameFilter`參數,例如,選擇名為"MyMethod"的所有公共虛擬方法。

## <a name="see-also"></a>另請參閱
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
