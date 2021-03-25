---
description: 取得陣列的順位或維度數目。
title: IDebugArrayField：： GetRank |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ac945e23090b649ffb5ad2f452ec9245aac81ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058972"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
取得陣列的順位或維度數目。

## <a name="syntax"></a>語法

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>參數
`pdwRank`\
擴展傳回排名。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 陣列的順位會對應至維度的數目。 在 c + + 和 c # 中，多維陣列其實是陣列的陣列，因此可以只被視為一維陣列 (而且 `GetRank` 方法一律會傳回 1) 。 另一方面，在中， [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 多維度陣列的處理方式不同，因此這類陣列的次序會反映 (的維度數目，而 `GetRank` 方法一律會傳回) 的維度數目。

## <a name="see-also"></a>另請參閱
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
