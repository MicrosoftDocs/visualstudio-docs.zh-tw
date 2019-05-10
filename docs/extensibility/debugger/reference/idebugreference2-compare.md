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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df878cc59a47a8d3cc7079f8b919f87d9bb60f43
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457455"
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

## <a name="parameters"></a>參數
 `dwCompare`\

 [in]值，以從[REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)列舉，指定的比較作業，例如，等於、 小於或大於。

 `pReference`\

 [in][IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，表示要比較的參考。

## <a name="return-value"></a>傳回值
 一律傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)