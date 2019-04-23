---
title: 範例實作的區域變數 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17de5858870afe3064f57cb51ec8b713bb65ddf9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047641"
---
# <a name="sample-implementation-of-locals"></a>區域變數的範例實作
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 以下是如何 Visual Studio 取得區域變數方法從運算式評估工具 (EE) 的概觀：

1. Visual Studio 會呼叫偵錯引擎 (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)若要取得[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)代表堆疊框架，包括區域變數的所有屬性的物件。

2. `IDebugStackFrame2::GetDebugProperty` 呼叫[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)以取得說明的方法，在其中發生中斷點的物件。 DE 提供符號提供者 ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md))、 地址 ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md))，並繫結器 ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md))。

3. `IDebugExpressionEvaluator::GetMethodProperty` 呼叫[GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)與提供`IDebugAddress`物件來取得[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)表示包含指定的位址的方法。

4. `IDebugContainerField`介面中查詢[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)介面。 這是此介面可存取方法的區域變數。

5. `IDebugExpressionEvaluator::GetMethodProperty` 具現化類別 (稱為`CFieldProperty`範例中) 執行`IDebugProperty2`介面代表方法的區域變數。 `IDebugMethodField`物件會置於這`CFieldProperty`物件連同`IDebugSymbolProvider`， `IDebugAddress`，和`IDebugBinder`物件。

6. 當`CFieldProperty`初始化物件時， [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md)上呼叫`IDebugMethodField`若要取得的物件[FIELD_INFO](../../extensibility/debugger/reference/field-info.md)結構，其中包含可顯示資訊的方法本身。

7. `IDebugExpressionEvaluator::GetMethodProperty` 會傳回`CFieldProperty`物件做為`IDebugProperty2`物件。

8. Visual Studio 呼叫[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)針對傳回`IDebugProperty2`篩選條件的物件`guidFilterLocalsPlusArgs`，就會傳回[IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件，包含方法的區域變數。 這個列舉型別會填入藉由呼叫[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)並[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)。

9. Visual Studio 呼叫[下一步](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)若要取得[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)每個本機的結構。 此結構包含一個指向`IDebugProperty2`本機介面。

10. Visual Studio 呼叫[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)的每個本機，以取得區域的名稱、 值和型別。 這項資訊會顯示在**區域變數**視窗。

## <a name="in-this-section"></a>本節內容
 [實作 GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)說明的實作[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)。

 [列舉區域變數](../../extensibility/debugger/enumerating-locals.md)描述如何偵錯引擎 (DE) 會呼叫列舉區域變數或引數。

 [取得本機屬性](../../extensibility/debugger/getting-local-properties.md)描述 DE 會呼叫，以取得名稱、 類型和值的一或多個區域變數的方式。

 [取得本機值](../../extensibility/debugger/getting-local-values.md)討論取得 local，這需要服務的評估內容所指定的繫結器物件的值。

 [評估區域變數](../../extensibility/debugger/evaluating-locals.md)說明評估區域變數的方式。

## <a name="related-sections"></a>相關章節
 [評估內容](../../extensibility/debugger/evaluation-context.md)提供 DE 呼叫運算式評估工具 (EE) 時所傳遞的引數。

 [MyCEE 範例](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f)示範建立 MyC 語言的運算式評估工具的其中一個實作方法。

## <a name="see-also"></a>另請參閱
- [顯示區域變數](../../extensibility/debugger/displaying-locals.md)