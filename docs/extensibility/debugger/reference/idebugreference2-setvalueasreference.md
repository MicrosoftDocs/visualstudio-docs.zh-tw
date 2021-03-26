---
description: 設定來自另一個參考的參考值。
title: IDebugReference2：： SetValueAsReference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c78da74368285c3dcfe06c13fdf8e665da0b7947
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075779"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
設定來自另一個參考的參考值。 保留供未來使用。

## <a name="syntax"></a>語法

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>參數
`rgpArgs`\
在 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 物件的陣列，用來決定如何設定參考值。

`dwArgCount`\
在陣列中的參考數目。

`pValue`\
在要設定屬性值的 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 物件。

`dwTimeout`\
在從這個方法傳回之前等候的最長時間（以毫秒為單位）。 使用 `INFINITE` 可無限期等候。

## <a name="return-value"></a>傳回值
 一律傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
