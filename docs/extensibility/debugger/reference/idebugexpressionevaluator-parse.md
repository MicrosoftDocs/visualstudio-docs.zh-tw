---
description: 這個方法會將運算式字串轉換為剖析的運算式。
title: IDebugExpressionEvaluator：:P arse |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6a586c7e7cac1a4ef034b7941840db59d376180
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152490"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
這個方法會將運算式字串轉換為剖析的運算式。

## <a name="syntax"></a>語法

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>參數
`upstrExpression`\
在要剖析的運算式字串。

`dwFlags`\
在 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) 常數的集合，可決定運算式的剖析方式。

`nRadix`\
在用來解讀任何數值資訊的基數。

`pbstrError`\
擴展以人們可讀取的文字形式傳回錯誤。

`pichError`\
擴展傳回運算式字串中錯誤開始的字元位置。

`ppParsedExpression`\
擴展傳回 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 物件中剖析的運算式。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會產生剖析的運算式，而不是實際值。 已剖析的運算式已可供評估，也就是轉換成值。

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
