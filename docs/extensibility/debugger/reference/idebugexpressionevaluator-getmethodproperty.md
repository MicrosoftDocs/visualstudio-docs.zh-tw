---
description: 這個方法會取得包含區域變數、引數和方法之其他屬性的屬性物件。
title: IDebugExpressionEvaluator：： GetMethodProperty |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d98e661ad3f469c41c120e07e6d54f76b089cb0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152503"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
這個方法會取得包含區域變數、引數和方法之其他屬性的屬性物件。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>參數
`pSymbolProvider`\
在要使用的符號提供者，以 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 物件表示。

`pAddress`\
在程式碼中的位址（以 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 物件表示）應解析為最接近的包含函式。

`pBinder`\
在要使用的系結器，以 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 物件表示。

`fIncludeHiddenLocals`\
在非零 (`TRUE`) 表示要包含隱藏的區域變數; 零 (`FALSE`) 表示離開隱藏的區域變數

`ppProperty`\
擴展傳回代表方法的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 隱藏的區域變數通常是由編譯器所產生的變數。

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
