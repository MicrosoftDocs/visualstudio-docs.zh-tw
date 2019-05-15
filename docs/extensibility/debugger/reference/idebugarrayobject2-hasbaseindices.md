---
title: IDebugArrayObject2::HasBaseIndices |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- HasBaseIndices
- IDebugArrayObject2::HasBaseIndices
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f37acdbfdeaeb076fb96d1aef27592e755eee99
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615114"
---
# <a name="idebugarrayobject2hasbaseindices"></a>IDebugArrayObject2::HasBaseIndices
判斷陣列是否具有定義的基底索引 （下限）。

## <a name="syntax"></a>語法

```cpp
HRESULT HasBaseIndices (
   BOOL* pfHasBaseIndices
);
```

```csharp
int HasBaseIndices (
   out bool pfHasBaseIndices
);
```

## <a name="parameters"></a>參數
`pfHasBaseIndices`\
[out]TRUE 表示指定的陣列，具有基底的索引 （下限）;否則為 FALSE。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。