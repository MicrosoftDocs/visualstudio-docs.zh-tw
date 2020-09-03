---
title: IDebugReference2：： GetDerivedMostReference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15e98884d040cfb2ebf1b33a56c7edea331fbff0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720610"
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
