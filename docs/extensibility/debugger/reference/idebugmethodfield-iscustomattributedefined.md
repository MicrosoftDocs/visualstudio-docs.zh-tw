---
title: IDebugMethod欄位:是自定義屬性定義 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d60e7a451a18ff8efbf47a008831109cd7f747c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727114"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
確定是否已定義特定的自定義屬性。

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
 如果在此方法上定義了自定義屬性,則返回S_OK,否則返回S_FALSE。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
