---
title: IDebugReference2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3ca4e944125f6673ca66accdb78742f693def77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869122"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
比較到另一個參考。 保留供未來使用。

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

#### <a name="parameters"></a>參數
 `dwCompare`

 [in]值，以從[REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)列舉，指定的比較作業，例如，等於、 小於或大於。

 `pReference`

 [in][IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，表示要比較的參考。

## <a name="return-value"></a>傳回值
 一律傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)