---
title: IDebugenumfield:從Stringcase敏感獲取價值 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730248"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
此方法使用不區分大小寫的搜索來返回與枚舉常量的名稱關聯的值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
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
 此方法不區分大小寫。 如果需要區分大小寫搜尋(例如,在名稱區分大小寫的C++)C++),請使用[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)。

## <a name="see-also"></a>另請參閱
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
