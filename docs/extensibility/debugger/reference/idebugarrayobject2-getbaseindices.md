---
description: 針對指定陣列中的維度數目的每個索引，抓取基底索引 (下限) 。
title: IDebugArrayObject2：： GetBaseIndices |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3ec8c0081205637ae228c426ac29d0523602439
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167785"
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
