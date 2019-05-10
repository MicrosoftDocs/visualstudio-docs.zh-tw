---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba770dec92054f68c3cb95433d2a2c83bdb37bce
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457513"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
取得參考的最具衍生性參考。 保留供未來使用。

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

 [out]傳回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，表示最具衍生性的屬性。

## <a name="return-value"></a>傳回值
 一律傳回 `E_NOTIMPL`。

## <a name="remarks"></a>備註
 例如，如果這個屬性會描述該物件會實作`ClassRoot`這是實際的具現化，但`ClassDerived`衍生自`ClassRoot`，則這個方法會傳回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件代表參考`ClassDerived`物件。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)