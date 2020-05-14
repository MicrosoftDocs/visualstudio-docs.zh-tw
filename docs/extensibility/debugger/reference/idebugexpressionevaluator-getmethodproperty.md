---
title: IDebug運算式評估器::獲取方法屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebcf24ee39505091ff79c1f2f31d505217f77efb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729512"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
此方法獲取包含方法的局部變數、參數和其他屬性的屬性物件。

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
[在]要使用的符號提供者,表示為[IDebugSymbol 提供程式](../../../extensibility/debugger/reference/idebugsymbolprovider.md)物件。

`pAddress`\
[在]代碼中的位址(表示為[IDebugAddress 物件](../../../extensibility/debugger/reference/idebugaddress.md))應解析為最近的包含函數。

`pBinder`\
[在]要使用的活頁夾,表示為[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件。

`fIncludeHiddenLocals`\
[在]非零`TRUE`() 表示包括隱藏的局部變數;零`FALSE`( ) 意味著排除隱藏的當地人

`ppProperty`\
[出]返回表示方法的[IDebug Property2](../../../extensibility/debugger/reference/idebugproperty2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 隱藏的局部變數通常是編譯器生成的變數。

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
