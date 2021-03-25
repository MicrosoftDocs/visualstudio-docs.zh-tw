---
description: 針對指定陣列中的維度數目的每個索引，抓取基底索引 (下限) 。
title: IDebugArrayObject2：： GetBaseIndices |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3843b93bb9255c28b8ca083af37a3ba4ecbd7f7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067552"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
針對指定陣列中的維度數目的每個索引，抓取基底索引 (下限) 。

## <a name="syntax"></a>語法

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

## <a name="parameters"></a>參數
`dwRank`\
在陣列 (等級) 的維度數目。

`dwIndices`\
擴展基底索引 (陣列的下限) 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 例如，此函式會針對下列 c # 程式碼所建立的陣列傳回 ' 5 '：

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
