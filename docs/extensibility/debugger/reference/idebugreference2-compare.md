---
title: IDebug參考2::比較 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d293fcb89c92a19acc4f5a3910015914ef4231a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720647"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
將一個引用與另一個引用進行比較。 保留供未來使用。

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
[在][REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)枚舉中指定比較操作的值,例如,等於、小於或大於。

`pReference`\
[在]表示要比較的引用的[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件。

## <a name="return-value"></a>傳回值
 永遠會傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
