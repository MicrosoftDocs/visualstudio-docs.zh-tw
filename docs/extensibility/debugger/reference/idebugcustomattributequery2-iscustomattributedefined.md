---
title: IDebug自定義屬性查詢2::是自定義屬性定義 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7be649a5d65f88d8263bbe8950fda1a157855ed2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732543"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
確定自定義屬性是否存在名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>參數
`pszCustomAttributeName`\
[在]包含要尋找的自訂屬性的名稱的字串。

## <a name="return-value"></a>傳回值
 如果在此欄位上定義了自定義屬性,則返回S_OK,否則返回S_FALSE。

## <a name="remarks"></a>備註
 要取得與自定義屬性關聯的屬性位元組,請呼叫[GetCustom屬性ByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
