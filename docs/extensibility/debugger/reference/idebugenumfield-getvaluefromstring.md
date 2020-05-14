---
title: IDebugenumfield:從String中獲得價值 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb340721c9f446b740c2723dc3f6dc05452e74de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730268"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
此方法返回與枚舉常量的名稱關聯的值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>參數
`pszValue`\
[在]指定要取得值的名稱的字串。 請注意,對於C++,這是一個寬字元字串。

`pValue`\
[出]返回關聯的數值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,如果`S_FALSE`名稱不是枚舉的一部分,則返回或錯誤代碼。

## <a name="remarks"></a>備註
 此方法區分大小寫。 如果需要不區分大小寫的搜尋(例如,在名稱不區分大小寫的 Visual Basic 等語言中),請使用[GetValue FromStringCase 對內敏感](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)。

## <a name="see-also"></a>另請參閱
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
