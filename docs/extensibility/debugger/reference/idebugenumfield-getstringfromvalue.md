---
title: IDebugenumfield::從價值中獲取字串 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de59c573f7e233ea2aacb0dfa38826051c59373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730282"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
此方法獲取給定其值的枚舉常量的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>參數
`value`\
[在]要獲取枚舉常量名稱的值。

`pbstrValue`\
[出]返回枚舉常量的名稱。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,如果`S_FALSE`值沒有關聯名稱,則返回,或者返回錯誤代碼。

## <a name="remarks"></a>備註
 如果有多個名稱與同一值關聯,則將返回枚舉中定義的第一個名稱。

## <a name="see-also"></a>另請參閱
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
