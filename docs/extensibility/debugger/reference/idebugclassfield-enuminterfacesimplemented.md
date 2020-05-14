---
title: IDebugClassfield:實現枚舉介面 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734482"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
為此類實現的介面創建枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]返回表示已實現介面清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件。 如果沒有介面,則返回 null 值。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK或返回S_FALSE如果此類上沒有實現介面。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 枚舉的每個元素都是描述介面的[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件。 請注意,非託管[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]代碼不使用介面作為離散實體,因此此方法始終返回非託管[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]代碼的 null 值。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
