---
description: 此介面代表運算式評估工具。
title: IDebugExpressionEvaluator |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dd14e85d279bd724dcfdf2cd9b71028ac5a4fd87
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092068"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

此介面代表運算式評估工具。

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
運算式評估工具必須執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
若要取得這個介面，請 `CoCreateInstance` 使用評估工具 (CLSID) 的類別識別碼，透過方法具現化運算式評估工具。 請參閱範例。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDebugExpressionEvaluator` 。

|方法|描述|
|------------|-----------------|
|[剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|將運算式字串轉換為剖析的運算式。|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|取得方法的區域變數、引數和其他屬性。|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|將方法位置和位移轉換成記憶體位址。|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|決定要用來建立可列印結果的語言。|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|設定登錄根目錄。 用於並存的偵錯工具。|

## <a name="remarks"></a>備註
在一般情況下，debug engine (DE) 會將運算式評估工具具現化 (EE) ，因為 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)呼叫的結果。 因為 DE 知道它想要使用的 EE 語言和廠商，所以會從登錄取得 EE 的 CLSID ([SDK helper For 偵錯工具，以](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `GetEEMetric` 協助進行此抓取) 。

當 EE 具現化之後，DE 會呼叫 [parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 來剖析運算式，並將它儲存在 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 物件中。 之後，呼叫 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 會評估運算式。

## <a name="requirements"></a>規格需求
標頭： ee. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>範例
這個範例示範如何在指定符號提供者和原始程式碼中的位址時，將運算式評估工具具現化。 此範例使用 `GetEEMetric` [SDK Helper for 偵錯工具](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) dbgmetric 的函式。

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
