---
title: IDebugExpression評估器::P微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1af9d3f253a9849f54bb5a50d432b98eb4ad7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729501"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
此方法將表達式字串轉換為解析的運算式。

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
[在]要解析的表達式字串。

`dwFlags`\
[在][PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)常量的集合,用於確定如何解析運算式。

`nRadix`\
[在]用於解釋任何數值資訊的 Radix。

`pbstrError`\
[出]將錯誤作為人可讀文字返回。

`pichError`\
[出]傳回表示式字串中錯誤開始位置的字元位置。

`ppParsedExpression`\
[出]返回[IDebugParsed 表示式](../../../extensibility/debugger/reference/idebugparsedexpression.md)物件中的解析表達式。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法生成解析的表達式,而不是實際值。 已解析的表達式已準備好進行計算,即轉換為值。

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
