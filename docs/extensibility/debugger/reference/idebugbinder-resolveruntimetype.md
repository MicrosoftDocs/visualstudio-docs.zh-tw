---
title: IDebugBinder::解析運行時類型 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bdbff651618365f3b68a142a6cb1e76836876a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735950"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
此方法確定物件的運行時類型。

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
[在]要剖析的[IDebug 物件](../../../extensibility/debugger/reference/idebugobject.md)。

`ppResolved`\
[出]將對象的類型作為[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)返回。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 對象的運行時類型在編譯時並不總是已知的。 例如,使用多態性,可以將參數作為基類傳遞給函數,如按鈕類。 實際參數可能是派生類,如單選按鈕類。

## <a name="see-also"></a>另請參閱
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
