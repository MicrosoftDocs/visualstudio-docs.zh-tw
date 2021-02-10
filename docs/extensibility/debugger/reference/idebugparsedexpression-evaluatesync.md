---
title: IDebugParsedExpression：： EvaluateSync |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ff14c10f5563053ce704982455eee6d9dc81b742
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953249"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
這個方法會評估剖析的運算式，並選擇性地將結果轉換成另一種資料類型。

## <a name="syntax"></a>語法

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>參數
`dwEvalFlags`\
在 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 常數的組合，可控制運算式的評估方式。

`dwTimeout`\
在指定從這個方法傳回之前等候的最長時間（以毫秒為單位）。 使用 `INFINITE` 可無限期等候。

`pSymbolProvider`\
在符號提供者，以 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 介面表示。

`pAddress`\
在方法內目前的執行位置，以 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面表示。

`pBinder`\
在系結器，以 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 介面表示。

`bstrResultType`\
在結果應轉換成的類型。 這個引數可以是 null 值。

`ppResult`\
擴展傳回代表評估結果的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 運算式評估內容是由提供 `pAddress` ，可讓您判斷包含方法，然後使用語言範圍規則來判斷運算式中的符號值。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
