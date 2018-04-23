---
title: 範例實作的區域變數 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56ac92989abe929884ac029e3b9c9c7dafad5fd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sample-implementation-of-locals"></a>範例實作的區域變數
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 以下是 Visual Studio 從運算式評估工具 (EE) 所取得的方法的區域變數的概觀：  
  
1.  Visual Studio 會呼叫偵錯引擎 (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)取得[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件，代表堆疊框架，包括 [區域變數] 的所有屬性。  
  
2.  `IDebugStackFrame2::GetDebugProperty` 呼叫[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)取得物件，描述在其中發生中斷點的方法。 DE 提供符號提供者 ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md))，地址 ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md))，和繫結器 ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md))。  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` 呼叫[GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)及所提供`IDebugAddress`物件取得[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)代表包含指定的位址的方法。  
  
4.  `IDebugContainerField`介面針對查詢[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)介面。 這個介面，可讓方法的 [區域變數] 存取它。  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` 具現化類別 (稱為`CFieldProperty`範例中)，用來實作`IDebugProperty2`介面代表方法的區域變數。 `IDebugMethodField`物件會放置在這個`CFieldProperty`物件連同`IDebugSymbolProvider`，`IDebugAddress`和`IDebugBinder`物件。  
  
6.  當`CFieldProperty`物件已初始化， [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md)上呼叫`IDebugMethodField`物件取得[FIELD_INFO](../../extensibility/debugger/reference/field-info.md)包含本身的方法可顯示所有資訊的結構.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` 傳回`CFieldProperty`物件當做`IDebugProperty2`物件。  
  
8.  Visual Studio 呼叫[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)針對傳回`IDebugProperty2`與篩選條件的物件`guidFilterLocalsPlusArgs`。 這會傳回[IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件，其中包含方法的區域變數。 這個列舉型別會填入呼叫[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)和[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)。  
  
9. Visual Studio 呼叫[下一步](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)取得[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)每個區域的結構。 此結構包含的指標`IDebugProperty2`本機介面。  
  
10. Visual Studio 呼叫[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)每個本機取得區域的名稱、 值和類型。 這是顯示在資訊**區域變數**視窗。  
  
## <a name="in-this-section"></a>本節內容  
 [實作 GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 說明的實作[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)。  
  
 [列舉區域變數](../../extensibility/debugger/enumerating-locals.md)  
 描述如何偵錯引擎 (DE) 會呼叫列舉本機變數或引數。  
  
 [取得區域變數的屬性](../../extensibility/debugger/getting-local-properties.md)  
 描述如何 DE 進行呼叫，以取得名稱、 類型和值的一個或多個區域變數。  
  
 [取得區域變數值](../../extensibility/debugger/getting-local-values.md)  
 討論取得 local，這需要服務的評估內容所指定的繫結器物件的值。  
  
 [評估區域變數](../../extensibility/debugger/evaluating-locals.md)  
 說明如何評估 [區域變數]。  
  
## <a name="related-sections"></a>相關章節  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 提供 DE 呼叫運算式評估工具 (EE) 時，會傳遞的引數。  
  
 [MyCEE 範例](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 示範建立 MyC 語言的運算式評估工具的其中一個實作方法。  
  
## <a name="see-also"></a>另請參閱  
 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)