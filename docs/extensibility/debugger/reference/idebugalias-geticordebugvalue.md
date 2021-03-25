---
description: 抓取 managed 程式碼介面，此介面表示與此別名相關聯的值。
title: IDebugAlias：： GetICorDebugValue |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad6cd04d077245d3e893099aab8820ddc8ccf559
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095910"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
抓取 managed 程式碼介面，此介面表示與此別名相關聯的值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>參數
`ppUnk`\
[out] `IUnknown` 介面，表示與此別名相關聯的值。 此介面可針對介面進行查詢 `ICorDebugValue` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法只會套用至 managed 值 (`ICorDebugValue` 是 .NET Framework 中可用的介面，而且是在) cordebug.h 檔案的 .NET FRAMEWORK SDK 中定義。

## <a name="see-also"></a>另請參閱
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
