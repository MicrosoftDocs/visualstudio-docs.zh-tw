---
description: 這個方法會根據指定的值來取得列舉常數的名稱。
title: IDebugEnumField：： GetStringFromValue |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41d004a9b226646dd1196f1debc244cdf11efe32
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092575"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
這個方法會根據指定的值來取得列舉常數的名稱。

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
在要取得列舉常數名稱的值。

`pbstrValue`\
擴展傳回列舉常數的名稱。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則， `S_FALSE` 如果值沒有相關聯的名稱，則傳回，否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果有多個與相同值相關聯的名稱，則會傳回列舉中所定義的第一個名稱。

## <a name="see-also"></a>另請參閱
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
