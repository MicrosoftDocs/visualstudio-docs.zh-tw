---
title: IDebug運算式評估器 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729381"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

此介面表示表達式賦值器。

## <a name="syntax"></a>語法

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
表達式賦值器必須實現此介面。

## <a name="notes-for-callers"></a>通話備註
要獲取此介面,請使用賦值器的類 ID (CLSID) 通過`CoCreateInstance`方法實例化運算式賦值器。 請參閱示例。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法`IDebugExpressionEvaluator`。

|方法|描述|
|------------|-----------------|
|[剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|將運算式字串轉換為解析的運算式。|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|獲取方法的局部變數、參數和其他屬性。|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|將方法位置和偏移轉換為記憶體位址。|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|確定使用哪種語言來創建可列印的結果。|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|設置註冊表根。 用於並行調試。|

## <a name="remarks"></a>備註
在典型情況下,調試引擎 (DE) 實例化運算式賦值器 (EE) 作為調用[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)的結果。 由於 DE 知道要使用的 EE 的語言和供應商,因此 DE 從註冊表中獲取 EE 的 CLSID([用於除錯功能的 SDK 説明器](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md),`GetEEMetric`可幫助進行此檢索)。

實例化 EE 後,DE 調用[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)來解析表示式並將其存儲在[IDebugParsed 運算式](../../../extensibility/debugger/reference/idebugparsedexpression.md)物件中。 稍後,對[評估同步](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)的調用將計算表達式。

## <a name="requirements"></a>需求
標題: ee.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="example"></a>範例
此示例演示如何實例化在原始碼中給定符號提供程式和位址的運算式賦值器。 本示例使用用於除錯庫`GetEEMetric`的[SDK 幫助器](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)的函數 dbgmetric.lib。

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
