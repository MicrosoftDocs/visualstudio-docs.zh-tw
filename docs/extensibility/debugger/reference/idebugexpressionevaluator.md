---
title: "IDebugExpressionEvaluator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator 介面"
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugExpressionEvaluator
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面表示運算式評估工具。  
  
## 語法  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## 實作者注意事項  
 運算式評估工具必須實作這個介面。  
  
## 呼叫端資訊  
 若要取得此介面，具現化運算式評估工具，透過 `CoCreateInstance` 方法藉由使用 「 評估工具的類別識別碼 \(CLSID\)。 請參閱範例。  
  
## 依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugExpressionEvaluator`。  
  
|方法|描述|  
|--------|--------|  
|[剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|將運算式字串轉換成剖析的運算式。|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|取得本機變數、 引數和其他屬性的方法。|  
|[GetMethodLocationProperty](../Topic/IDebugExpressionEvaluator::GetMethodLocationProperty.md)|將方法的位置和位移轉換到的記憶體位址。|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|決定要用來建立可列印結果的語言。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|設定的登錄根目錄。 使用的並行偵錯。|  
  
## 備註  
 在典型的情況下，偵錯引擎 \(DE\) 具現化運算式評估工具 \(EE\) 由於呼叫 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)。 由於 DE 知道的語言和 EE 它要使用的供應商，DE 會從登錄取得 EE CLSID \( [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 函式， `GetEEMetric`, ，幫助使用這項擷取\)。  
  
 DE EE 具現化後，呼叫 [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 剖析運算式，並將它存放在 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 物件。 更新版本中，呼叫 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 會評估運算式。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 範例  
 這個範例示範如何具現化運算式評估工具的原始程式碼中指定的符號提供者和地址。 這個範例會使用函式， `GetEEMetric`, ，從 [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 程式庫、 dbgmetric.lib。  
  
```cpp#  
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
            CLSID clsidEE      = { 0 };  
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
  
## 請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)