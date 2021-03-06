---
description: 這個方法會判斷物件的執行時間類型。
title: IDebugBinder：： ResolveRuntimeType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23bc63e4550264d499c6d97a03aa9361b3fa4f62
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067344"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
這個方法會判斷物件的執行時間類型。

## <a name="syntax"></a>語法

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>參數
`pObject`\
在要解析的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 。

`ppResolved`\
擴展傳回物件的型別為 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 在編譯時間，物件的執行時間類型不一定是已知的。 例如，使用多型，可以將引數傳遞至函式作為其基類，例如按鈕類別。 實際的引數可能是衍生類別，例如選項按鈕類別。

## <a name="see-also"></a>另請參閱
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
