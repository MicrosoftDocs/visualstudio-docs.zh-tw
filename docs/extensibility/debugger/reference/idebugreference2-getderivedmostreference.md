---
description: 取得參考的衍生最多參考。
title: IDebugReference2：： GetDerivedMostReference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c482b05620f280b2948aefe7e95eb38682268c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071437"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
取得參考的衍生最多參考。 保留供未來使用。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>參數
`ppDerivedMost`\
擴展傳回 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 物件，這個物件表示衍生的最多屬性。

## <a name="return-value"></a>傳回值
 一律傳回 `E_NOTIMPL`。

## <a name="remarks"></a>備註
 例如，如果這個屬性描述的物件會執行， `ClassRoot` 但實際上是 `ClassDerived` 衍生自的具現化 `ClassRoot` ，則這個方法會傳回代表物件參考的 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 物件 `ClassDerived` 。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
