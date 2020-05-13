---
title: IDebugsers運算式::評估同步 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726016"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
此方法計算解析的運算式,並選擇性地將結果轉換為另一種數據類型。

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
[在][EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)常量的組合,用於控制運算式計算方式。

`dwTimeout`\
[在]指定從此方法返回之前等待的最大時間(以毫秒為單位)。 用於`INFINITE`無限期等待。

`pSymbolProvider`\
[在]符號提供程式,表示為[IDebugSymbol 提供程式](../../../extensibility/debugger/reference/idebugsymbolprovider.md)介面。

`pAddress`\
[在]方法中的目前執行位置,表示為[IDebugAddress 介面](../../../extensibility/debugger/reference/idebugaddress.md)。

`pBinder`\
[在]活頁夾,表示為[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面。

`bstrResultType`\
[在]結果應強制轉換為的類型。 這裡可以是 null 值。

`ppResult`\
[出]返回表示評估結果的[IDebug Property2](../../../extensibility/debugger/reference/idebugproperty2.md)介面。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 運算式計算上下文由`pAddress`提供 ,這樣就可以確定包含方法,然後使用語言範圍規則來確定表達式中符號的值。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
