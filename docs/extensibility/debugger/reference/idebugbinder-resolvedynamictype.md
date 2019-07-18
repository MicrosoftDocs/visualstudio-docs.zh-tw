---
title: IDebugBinder::ResolveDynamicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveDynamicType
helpviewer_keywords:
- IDebugBinder::ResolveDynamicType method
ms.assetid: 2c36ef92-5b44-4cfd-988e-54a2e5a6710c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6f07643c836bd2ca1cea35659bd1b38cf72dbe45
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313191"
---
# <a name="idebugbinderresolvedynamictype"></a>IDebugBinder::ResolveDynamicType
這個方法會傳回變數的確切型別。

## <a name="syntax"></a>語法

```cpp
HRESULT ResolveDynamicType (
   IDebugDynamicField *pDynamic,
   IDebugField       **ppResolved
);
```

```csharp
int ResolveDynamicType(
   IDebugDynamicField pDynamic,
   out IDebugField    ppResolved
);
```

## <a name="parameters"></a>參數
`pDynamic`\
[in][IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)代表變數的類型。

`ppResolved`\
[out]傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)提供變數的類型的特定資訊。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)