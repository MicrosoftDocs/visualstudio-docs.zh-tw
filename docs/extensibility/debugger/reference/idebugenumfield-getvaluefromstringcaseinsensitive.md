---
description: 這個方法會使用不區分大小寫的搜尋，傳回與列舉常數名稱相關聯的值。
title: IDebugEnumField：： GetValueFromStringCaseInsensitive |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80ded5237cfc0fe1b03ae5175ca0c92a188538ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065982"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
這個方法會使用不區分大小寫的搜尋，傳回與列舉常數名稱相關聯的值。

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
在字串，指定要取得其值的名稱。 請注意，在 c + + 中，這是寬字元字串。

`pValue`\
擴展傳回相關聯的數值。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則， `S_FALSE` 如果名稱不是列舉的一部分或錯誤碼，則會傳回。

## <a name="remarks"></a>備註
 這個方法不區分大小寫。 如果需要區分大小寫的搜尋 (例如，使用 c + + 的語言，其中名稱會區分大小寫) ，請使用 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)。

## <a name="see-also"></a>另請參閱
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
