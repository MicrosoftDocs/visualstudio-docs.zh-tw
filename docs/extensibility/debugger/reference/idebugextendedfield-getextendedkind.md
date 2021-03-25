---
description: 抓取指定的延伸欄位種類。
title: IDebugExtendedField：： GetExtendedKind |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91438d87a59c94efd837389229cb107e81573f12
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077209"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
抓取指定的延伸欄位種類。

## <a name="syntax"></a>語法

```cpp
HRESULT GetExtendedKind(
   FIELD_KIND_EX* pdwKind
);
```

```csharp
int GetExtendedKind(
   ref enum_FIELD_KIND_EX pdwKind
);
```

## <a name="parameters"></a>參數
`pdwKind`\
[in，out] [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) 列舉中的值，可定義欄位的種類。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
