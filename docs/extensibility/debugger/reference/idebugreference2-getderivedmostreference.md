---
title: IDebug 參考2::獲取最參考 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720610"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
獲取引用的派生最大引用。 保留供未來使用。

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
[出]返回表示派生最派生屬性的[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件。

## <a name="return-value"></a>傳回值
 永遠會傳回 `E_NOTIMPL`。

## <a name="remarks"></a>備註
 例如,如果`ClassRoot`此屬性描述實現但實際上是派生自`ClassDerived``ClassRoot`的物件的物件,則此方法返回表示對物件的引用`ClassDerived`的[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
