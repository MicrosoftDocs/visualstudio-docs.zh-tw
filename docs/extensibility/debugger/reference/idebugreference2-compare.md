---
description: 比較某個參考與另一個參考。
title: IDebugReference2：： Compare |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef006cba574e0cc5f51d2ec45eb6187b1076543a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166003"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
比較某個參考與另一個參考。 保留供未來使用。

## <a name="syntax"></a>語法

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>參數
`dwCompare`\
在 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) 列舉中的值，可指定比較作業，例如，等於、小於或大於。

`pReference`\
在 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 物件，表示要比較的參考。

## <a name="return-value"></a>傳回值
 一律傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
